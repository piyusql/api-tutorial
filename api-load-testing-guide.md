# API Load Testing Guide with Locust

> **A comprehensive guide to load testing your APIs before releasing to production.**
>
> This guide is a companion to the [API Handbook](./api-handbook.md).

---

## Table of Contents

- [Why Load Testing is Essential](#why-load-testing-is-essential)
- [What is Locust?](#what-is-locust)
- [Installation](#installation)
- [Your First Locust Test](#your-first-locust-test)
- [Running Locust](#running-locust)
- [Understanding Locust Metrics](#understanding-locust-metrics)
- [Comprehensive Load Test Example](#comprehensive-load-test-example)
- [Load Testing Scenarios](#load-testing-scenarios)
  - [Baseline Performance Test](#scenario-1-baseline-performance-test)
  - [Stress Test](#scenario-2-stress-test-find-breaking-point)
  - [Spike Test](#scenario-3-spike-test-sudden-traffic-surge)
  - [Soak Test](#scenario-4-soak-test-endurance)
- [Distributed Load Testing](#distributed-load-testing)
- [CI/CD Integration](#cicd-integration)
- [Load Testing Best Practices](#load-testing-best-practices)
- [Pre-Release Checklist](#pre-release-load-testing-checklist)
- [Golden Rules](#load-testing-golden-rules)

---

## Why Load Testing is Essential

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                    THE LOAD TESTING REALITY CHECK                           │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ❌ Without Load Testing:                                                   │
│     • API crashes during product launch                                    │
│     • Black Friday takes down your e-commerce site                         │
│     • Viral moment becomes a disaster                                      │
│     • You discover bottlenecks in production (too late!)                   │
│     • Customers leave, never to return                                     │
│                                                                             │
│  ✅ With Load Testing:                                                      │
│     • Know exact capacity limits                                           │
│     • Identify bottlenecks before launch                                   │
│     • Plan infrastructure scaling                                          │
│     • Set realistic rate limits                                            │
│     • Sleep well on launch night                                           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Real-world examples of load testing failures:**

| Company | What Happened | Cost |
|---------|---------------|------|
| Healthcare.gov | Crashed on launch day | $1.7 billion to fix |
| Target | Black Friday outage | Millions in lost sales |
| Pokemon Go | Server overload at launch | Delayed global rollout |

---

## What is Locust?

[Locust](https://locust.io) is a modern, Python-based load testing tool that lets you define user behavior in code.

**Why Locust?**
- ✅ Write tests in Python (you already know it!)
- ✅ Distributed testing across multiple machines
- ✅ Real-time web UI for monitoring
- ✅ Highly scalable (millions of users)
- ✅ Open source and free
- ✅ Easy to integrate with CI/CD

**Alternatives:**
- **k6** - JavaScript-based, great for developers
- **JMeter** - Java-based, GUI-heavy, enterprise standard
- **Gatling** - Scala-based, good for complex scenarios
- **Artillery** - Node.js-based, YAML configuration

---

## Installation

```bash
# Install Locust
pip install locust

# Verify installation
locust --version

# Optional: Install with extra features
pip install locust[gevent]  # Better performance
```

**Requirements:**
- Python 3.8+
- pip

---

## Your First Locust Test

Create a file called `locustfile.py`:

```python
"""
locustfile.py - Basic Load Test for a REST API
"""
from locust import HttpUser, task, between

class APIUser(HttpUser):
    """
    Simulates a user interacting with our API.
    Each user will execute tasks randomly based on their weights.
    """

    # Wait 1-3 seconds between tasks (simulates real user behavior)
    wait_time = between(1, 3)

    # Called once when a user starts
    def on_start(self):
        """Login and get authentication token"""
        response = self.client.post("/auth/login", json={
            "email": "test@example.com",
            "password": "testpassword123"
        })
        if response.status_code == 200:
            self.token = response.json().get("access_token")
            self.client.headers.update({
                "Authorization": f"Bearer {self.token}"
            })
        else:
            self.token = None

    @task(10)  # Weight of 10 - most common operation
    def list_users(self):
        """GET /api/v1/users - List users (most frequent)"""
        self.client.get("/api/v1/users")

    @task(5)  # Weight of 5 - moderately common
    def get_single_user(self):
        """GET /api/v1/users/{id} - Get specific user"""
        user_id = 1  # In real tests, randomize this
        self.client.get(f"/api/v1/users/{user_id}")

    @task(2)  # Weight of 2 - less common
    def search_users(self):
        """GET /api/v1/users/search - Search users"""
        self.client.get("/api/v1/users/search?q=john")

    @task(1)  # Weight of 1 - rare operation
    def create_user(self):
        """POST /api/v1/users - Create user (least frequent)"""
        self.client.post("/api/v1/users", json={
            "name": "Load Test User",
            "email": f"loadtest_{self.environment.runner.user_count}@example.com"
        })
```

### Key Concepts:

| Concept | Description |
|---------|-------------|
| `HttpUser` | Base class for simulating HTTP users |
| `@task(weight)` | Decorator to define user actions. Higher weight = more frequent |
| `wait_time` | Time between tasks (simulates think time) |
| `on_start()` | Called once when user starts (good for login) |
| `on_stop()` | Called when user stops (good for cleanup) |
| `self.client` | HTTP client for making requests |

---

## Running Locust

### Web UI Mode (Interactive)

```bash
# Start Locust with web UI
locust -f locustfile.py --host=http://localhost:8000

# Open browser to http://localhost:8089
# Set number of users and spawn rate, then start!
```

### Headless Mode (CI/CD)

```bash
# Run without UI - perfect for automation
locust -f locustfile.py \
    --host=http://localhost:8000 \
    --users 100 \
    --spawn-rate 10 \
    --run-time 5m \
    --headless

# With CSV output
locust -f locustfile.py \
    --host=http://localhost:8000 \
    --users 100 \
    --spawn-rate 10 \
    --run-time 5m \
    --headless \
    --csv=results \
    --html=report.html
```

### Command Line Options

| Option | Description | Example |
|--------|-------------|---------|
| `-f` | Locust file path | `-f locustfile.py` |
| `--host` | Target host URL | `--host=http://api.example.com` |
| `--users` | Total users to simulate | `--users 100` |
| `--spawn-rate` | Users to spawn per second | `--spawn-rate 10` |
| `--run-time` | Test duration | `--run-time 5m` |
| `--headless` | Run without web UI | `--headless` |
| `--csv` | CSV output prefix | `--csv=results` |
| `--html` | HTML report path | `--html=report.html` |

---

## Understanding Locust Metrics

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         KEY METRICS TO WATCH                                │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  RESPONSE TIME                                                              │
│  ─────────────                                                              │
│  • Median (50th percentile) - Typical user experience                      │
│  • 95th percentile (p95) - Worst case for most users                       │
│  • 99th percentile (p99) - Edge cases                                      │
│  • Max - Absolute worst case                                               │
│                                                                             │
│  TARGET: p95 < 500ms for most APIs                                         │
│                                                                             │
│  THROUGHPUT                                                                 │
│  ──────────                                                                 │
│  • Requests per second (RPS) - How many requests your API handles          │
│  • Users - Concurrent users being simulated                                │
│                                                                             │
│  FAILURES                                                                   │
│  ────────                                                                   │
│  • Failure rate - Percentage of failed requests                            │
│  • Error types - What's failing (timeouts, 500s, etc.)                     │
│                                                                             │
│  TARGET: < 1% failure rate under normal load                               │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Why Percentiles Matter

```
Don't use averages! They hide problems.

Example: 100 requests
- 99 requests: 50ms
- 1 request: 5000ms (timeout)

Average: 99.5ms  ← Looks fine!
p99: 5000ms      ← Shows the real problem!
```

### Performance Targets

| Metric | Good | Acceptable | Poor |
|--------|------|------------|------|
| p50 (median) | < 100ms | < 200ms | > 500ms |
| p95 | < 300ms | < 500ms | > 1000ms |
| p99 | < 500ms | < 1000ms | > 2000ms |
| Error rate | < 0.1% | < 1% | > 1% |

---

## Comprehensive Load Test Example

```python
"""
locustfile.py - Production-Ready Load Test Suite
"""
from locust import HttpUser, task, between, events
from locust.runners import MasterRunner
import random
import string
import logging
import time

# Configure logging
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)


class AuthenticatedAPIUser(HttpUser):
    """
    Simulates an authenticated user performing typical API operations.
    """
    wait_time = between(1, 3)

    # Test data
    test_users = []

    def on_start(self):
        """Authenticate before starting tests"""
        self.authenticate()

    def authenticate(self):
        """Get JWT token for authenticated requests"""
        response = self.client.post(
            "/api/v1/auth/login",
            json={
                "email": "loadtest@example.com",
                "password": "LoadTest123!"
            },
            name="/api/v1/auth/login"  # Group in stats
        )

        if response.status_code == 200:
            data = response.json()
            self.token = data.get("access_token")
            self.client.headers.update({
                "Authorization": f"Bearer {self.token}"
            })
            logger.info("Authentication successful")
        else:
            logger.error(f"Authentication failed: {response.status_code}")
            self.token = None

    # ============== READ OPERATIONS (Most Common) ==============

    @task(20)
    def list_items_paginated(self):
        """Test paginated list endpoint - most common operation"""
        page = random.randint(1, 10)
        limit = random.choice([10, 20, 50])

        with self.client.get(
            f"/api/v1/items?page={page}&limit={limit}",
            name="/api/v1/items?page=N&limit=N",
            catch_response=True
        ) as response:
            if response.status_code == 200:
                data = response.json()
                if "data" in data and "pagination" in data:
                    response.success()
                else:
                    response.failure("Invalid response structure")
            else:
                response.failure(f"Status code: {response.status_code}")

    @task(15)
    def get_single_item(self):
        """Test single item retrieval"""
        item_id = random.randint(1, 1000)

        with self.client.get(
            f"/api/v1/items/{item_id}",
            name="/api/v1/items/{id}",
            catch_response=True
        ) as response:
            if response.status_code in [200, 404]:  # 404 is acceptable
                response.success()
            else:
                response.failure(f"Unexpected status: {response.status_code}")

    @task(10)
    def search_items(self):
        """Test search functionality"""
        search_terms = ["python", "api", "test", "data", "user"]
        query = random.choice(search_terms)

        self.client.get(
            f"/api/v1/items/search?q={query}",
            name="/api/v1/items/search"
        )

    # ============== WRITE OPERATIONS (Less Common) ==============

    @task(3)
    def create_item(self):
        """Test item creation"""
        random_suffix = ''.join(random.choices(string.ascii_lowercase, k=8))

        with self.client.post(
            "/api/v1/items",
            json={
                "name": f"Load Test Item {random_suffix}",
                "description": "Created during load testing",
                "price": round(random.uniform(10, 1000), 2)
            },
            name="/api/v1/items [POST]",
            catch_response=True
        ) as response:
            if response.status_code == 201:
                data = response.json()
                if "id" in data.get("data", {}):
                    # Store for later operations
                    self.test_users.append(data["data"]["id"])
                    response.success()
                else:
                    response.failure("No ID in response")
            elif response.status_code == 429:
                response.success()  # Rate limiting is expected
            else:
                response.failure(f"Status: {response.status_code}")

    @task(2)
    def update_item(self):
        """Test item update"""
        item_id = random.randint(1, 100)

        self.client.put(
            f"/api/v1/items/{item_id}",
            json={
                "name": f"Updated Item {item_id}",
                "price": round(random.uniform(10, 1000), 2)
            },
            name="/api/v1/items/{id} [PUT]"
        )

    @task(1)
    def delete_item(self):
        """Test item deletion (rare operation)"""
        if self.test_users:
            item_id = self.test_users.pop()
            self.client.delete(
                f"/api/v1/items/{item_id}",
                name="/api/v1/items/{id} [DELETE]"
            )


class HealthCheckUser(HttpUser):
    """
    Separate user class for health check monitoring.
    Runs independently to ensure API is responsive.
    """
    wait_time = between(5, 10)
    weight = 1  # Low weight - few of these users

    @task
    def health_check(self):
        """Monitor API health during load test"""
        with self.client.get(
            "/health",
            name="/health [monitor]",
            catch_response=True
        ) as response:
            if response.status_code == 200:
                response.success()
            else:
                response.failure(f"Health check failed: {response.status_code}")


class HeavyUser(HttpUser):
    """
    Simulates power users who make many requests.
    Use sparingly to test edge cases.
    """
    wait_time = between(0.1, 0.5)  # Very fast requests
    weight = 1  # Very few of these users

    @task
    def rapid_requests(self):
        """Simulate rapid-fire requests (tests rate limiting)"""
        self.client.get("/api/v1/items?limit=5")


# ============== EVENT HOOKS ==============

@events.test_start.add_listener
def on_test_start(environment, **kwargs):
    """Called when test starts"""
    logger.info("=" * 60)
    logger.info("LOAD TEST STARTING")
    logger.info(f"Target host: {environment.host}")
    logger.info("=" * 60)


@events.test_stop.add_listener
def on_test_stop(environment, **kwargs):
    """Called when test stops"""
    logger.info("=" * 60)
    logger.info("LOAD TEST COMPLETED")
    logger.info("=" * 60)


@events.request.add_listener
def on_request(request_type, name, response_time, response_length,
               response, context, exception, **kwargs):
    """Called for every request - use for custom logging"""
    if exception:
        logger.error(f"Request failed: {name} - {exception}")
    elif response.status_code >= 500:
        logger.warning(f"Server error: {name} - {response.status_code}")
```

---

## Load Testing Scenarios

### Scenario 1: Baseline Performance Test

Establish normal performance metrics with low load.

```python
"""
baseline_test.py - Establish performance baseline
Run: locust -f baseline_test.py --host=http://localhost:8000 --users 10 --spawn-rate 1 --run-time 5m --headless
"""
from locust import HttpUser, task, constant

class BaselineUser(HttpUser):
    """Low load to establish baseline metrics"""
    wait_time = constant(1)  # Exactly 1 second between requests

    @task
    def get_items(self):
        self.client.get("/api/v1/items?limit=20")
```

**When to use:** Before any other tests, to establish baseline metrics.

---

### Scenario 2: Stress Test (Find Breaking Point)

Push the API until it breaks to find capacity limits.

```python
"""
stress_test.py - Find the breaking point
Run: locust -f stress_test.py --host=http://localhost:8000 --users 500 --spawn-rate 50 --run-time 10m --headless
"""
from locust import HttpUser, task, constant

class StressUser(HttpUser):
    """High load to find breaking point"""
    wait_time = constant(0.1)  # 10 requests per second per user

    @task
    def hammer_api(self):
        self.client.get("/api/v1/items")
```

**When to use:** To find maximum capacity and breaking point.

**What to look for:**
- When does error rate spike above 1%?
- When does p95 exceed 1 second?
- What resource hits 100% first (CPU, memory, DB connections)?

---

### Scenario 3: Spike Test (Sudden Traffic Surge)

Simulate sudden traffic spikes (viral moment, marketing campaign).

```python
"""
spike_test.py - Simulate sudden traffic spike
"""
from locust import HttpUser, task, between, LoadTestShape

class SpikeUser(HttpUser):
    wait_time = between(1, 2)

    @task
    def normal_usage(self):
        self.client.get("/api/v1/items")


class SpikeTestShape(LoadTestShape):
    """
    Custom load shape that simulates a traffic spike.

    Timeline:
    - 0-2 min: Ramp up to 50 users
    - 2-3 min: Sudden spike to 200 users
    - 3-5 min: Maintain 200 users
    - 5-6 min: Drop back to 50 users
    - 6-8 min: Maintain 50 users
    """

    stages = [
        {"duration": 120, "users": 50, "spawn_rate": 1},    # Ramp up
        {"duration": 60, "users": 200, "spawn_rate": 50},   # Spike!
        {"duration": 120, "users": 200, "spawn_rate": 50},  # Maintain spike
        {"duration": 60, "users": 50, "spawn_rate": 50},    # Drop
        {"duration": 120, "users": 50, "spawn_rate": 1},    # Maintain normal
    ]

    def tick(self):
        run_time = self.get_run_time()

        for stage in self.stages:
            if run_time < stage["duration"]:
                return (stage["users"], stage["spawn_rate"])
            run_time -= stage["duration"]

        return None  # Stop the test
```

**When to use:** Before marketing campaigns, product launches, or any event that might cause traffic spikes.

---

### Scenario 4: Soak Test (Endurance)

Run for extended periods to find memory leaks and connection issues.

```bash
# Run for extended period to find memory leaks, connection issues
locust -f locustfile.py \
    --host=http://localhost:8000 \
    --users 50 \
    --spawn-rate 5 \
    --run-time 2h \
    --headless \
    --csv=soak_test_results
```

**When to use:** Before major releases to ensure stability over time.

**What to look for:**
- Memory usage increasing over time
- Response times degrading
- Database connection pool exhaustion
- File descriptor leaks

---

## Distributed Load Testing

For serious load testing, run Locust across multiple machines.

### Master/Worker Setup

```bash
# On master machine
locust -f locustfile.py --master --host=http://api.example.com

# On worker machines (run on multiple servers)
locust -f locustfile.py --worker --master-host=192.168.1.100
```

### Docker Compose for Local Distributed Testing

```yaml
# docker-compose.yml
version: '3.8'

services:
  master:
    image: locustio/locust
    ports:
      - "8089:8089"
    volumes:
      - ./:/mnt/locust
    command: -f /mnt/locust/locustfile.py --master -H http://api:8000

  worker:
    image: locustio/locust
    volumes:
      - ./:/mnt/locust
    command: -f /mnt/locust/locustfile.py --worker --master-host master
    deploy:
      replicas: 4  # Run 4 workers
```

```bash
# Start distributed test
docker-compose up --scale worker=4
```

---

## CI/CD Integration

### GitHub Actions Workflow

```yaml
# .github/workflows/load-test.yml
name: Load Test

on:
  push:
    branches: [main]
  schedule:
    - cron: '0 2 * * *'  # Nightly at 2 AM

jobs:
  load-test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.11'

      - name: Install dependencies
        run: |
          pip install locust

      - name: Start API server
        run: |
          pip install -r requirements.txt
          uvicorn app.main:app --host 0.0.0.0 --port 8000 &
          sleep 10  # Wait for server to start

      - name: Run load test
        run: |
          locust -f tests/load/locustfile.py \
            --host=http://localhost:8000 \
            --users 50 \
            --spawn-rate 10 \
            --run-time 2m \
            --headless \
            --csv=load_test_results \
            --html=load_test_report.html

      - name: Check results
        run: |
          # Fail if error rate > 1% or p95 > 500ms
          python tests/load/check_results.py load_test_results_stats.csv

      - name: Upload results
        uses: actions/upload-artifact@v3
        with:
          name: load-test-results
          path: |
            load_test_results*.csv
            load_test_report.html
```

### Automated Pass/Fail Script

```python
"""
check_results.py - Validate load test results
"""
import csv
import sys

def check_results(csv_file):
    with open(csv_file, 'r') as f:
        reader = csv.DictReader(f)

        for row in reader:
            if row['Name'] == 'Aggregated':
                failure_rate = float(row['Failure Count']) / float(row['Request Count']) * 100
                p95 = float(row['95%'])

                print(f"Failure Rate: {failure_rate:.2f}%")
                print(f"P95 Response Time: {p95:.0f}ms")

                if failure_rate > 1:
                    print("❌ FAILED: Error rate too high (> 1%)")
                    sys.exit(1)

                if p95 > 500:
                    print("❌ FAILED: P95 response time too high (> 500ms)")
                    sys.exit(1)

                print("✅ PASSED: Load test within acceptable limits")
                sys.exit(0)

if __name__ == "__main__":
    check_results(sys.argv[1])
```

---

## Load Testing Best Practices

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    LOAD TESTING BEST PRACTICES                             │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  BEFORE TESTING                                                            │
│  ───────────────                                                           │
│  □ Test against staging, not production (unless carefully planned)        │
│  □ Use realistic test data                                                │
│  □ Warm up the system before measuring                                    │
│  □ Disable rate limiting for capacity tests (or test separately)          │
│  □ Monitor server resources (CPU, memory, DB connections)                 │
│                                                                            │
│  DURING TESTING                                                            │
│  ──────────────                                                            │
│  □ Start with low load, gradually increase                                │
│  □ Watch for error rate spikes                                            │
│  □ Monitor response time percentiles (not just average)                   │
│  □ Check server logs for errors                                           │
│  □ Monitor database query performance                                     │
│                                                                            │
│  AFTER TESTING                                                             │
│  ─────────────                                                             │
│  □ Document baseline metrics                                              │
│  □ Identify bottlenecks                                                   │
│  □ Create performance budget (e.g., p95 < 500ms)                         │
│  □ Set up automated performance regression tests                          │
│  □ Plan capacity based on results                                         │
│                                                                            │
│  KEY METRICS TO TRACK                                                      │
│  ────────────────────                                                      │
│  □ Requests per second (RPS) at various user counts                       │
│  □ Response time percentiles (p50, p95, p99)                              │
│  □ Error rate under load                                                  │
│  □ Time to first byte (TTFB)                                              │
│  □ Concurrent user capacity                                               │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## Pre-Release Load Testing Checklist

```
┌────────────────────────────────────────────────────────────────────────────┐
│                    PRE-RELEASE LOAD TESTING CHECKLIST                      │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  SETUP                                                                     │
│  □ Locust installed and configured                                        │
│  □ Test scenarios written for all critical endpoints                      │
│  □ Realistic user behavior modeled (wait times, task weights)             │
│  □ Test data prepared                                                     │
│  □ Monitoring dashboards ready                                            │
│                                                                            │
│  TEST EXECUTION                                                            │
│  □ Baseline test completed (low load)                                     │
│  □ Load test completed (expected traffic)                                 │
│  □ Stress test completed (find breaking point)                            │
│  □ Spike test completed (sudden traffic surge)                            │
│  □ Soak test completed (extended duration - optional)                     │
│                                                                            │
│  RESULTS ANALYSIS                                                          │
│  □ P95 response time < 500ms under expected load                          │
│  □ Error rate < 1% under expected load                                    │
│  □ Breaking point identified and documented                               │
│  □ Bottlenecks identified (DB, CPU, memory, network)                      │
│  □ Capacity planning completed                                            │
│                                                                            │
│  SIGN-OFF                                                                  │
│  □ Results documented and shared with team                                │
│  □ Performance budget established                                         │
│  □ Automated load tests added to CI/CD                                    │
│  □ Alerting configured for performance degradation                        │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## Load Testing Golden Rules

```
┌────────────────────────────────────────────────────────────────────────────┐
│                      LOAD TESTING GOLDEN RULES                             │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                            │
│  1. Test BEFORE launch, not after the crash                               │
│                                                                            │
│  2. Your API is only as fast as its slowest endpoint                      │
│                                                                            │
│  3. Average response time lies - use percentiles (p95, p99)               │
│                                                                            │
│  4. Test with realistic data volumes and user patterns                    │
│                                                                            │
│  5. The database is usually the bottleneck                                │
│                                                                            │
│  6. Run load tests regularly, not just before launch                      │
│                                                                            │
│  7. Automate load tests in CI/CD to catch regressions                     │
│                                                                            │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## Quick Reference Commands

```bash
# Basic test with web UI
locust -f locustfile.py --host=http://localhost:8000

# Headless test (CI/CD)
locust -f locustfile.py --host=http://localhost:8000 \
    --users 100 --spawn-rate 10 --run-time 5m --headless

# With CSV and HTML output
locust -f locustfile.py --host=http://localhost:8000 \
    --users 100 --spawn-rate 10 --run-time 5m --headless \
    --csv=results --html=report.html

# Distributed: Master
locust -f locustfile.py --master --host=http://api.example.com

# Distributed: Worker
locust -f locustfile.py --worker --master-host=192.168.1.100
```

---

## Additional Resources

- [Locust Documentation](https://docs.locust.io/)
- [Locust GitHub](https://github.com/locustio/locust)
- [Performance Testing Best Practices](https://docs.locust.io/en/stable/writing-a-locustfile.html)

---

*This guide is part of the [API Handbook](./api-handbook.md). Return to the handbook for complete API development guidance.*
