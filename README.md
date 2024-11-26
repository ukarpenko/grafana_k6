# grafana_k6
Dashboard Overview

The Grafana dashboard for K6 displays the following metrics:

    Data Received (data_received)
        Total data received (in bytes) during the test.

    Data Sent (data_sent)
        Total data sent (in bytes) during the test.

    Errors (errors)
        Count of errors encountered during the test.

    HTTP Requests (http_reqs)
        Total number of HTTP requests made during the test.

    Virtual Users (vus)
        The current number of active virtual users during the test.

    Maximum Virtual Users (vus_max)
        The maximum number of virtual users active at any point during the test.

    HTTP Request Duration (http_req_duration)
        Time taken for HTTP requests, including sending, waiting, and receiving. Percentiles (e.g., P90, P95) are visualized for detailed performance analysis.

    HTTP Request Receiving (http_req_receiving)
        Time spent receiving the response from the server.

    HTTP Request Waiting (http_req_waiting)
        Time spent waiting for the server to respond.

    HTTP Request Sending (http_req_sending)
        Time spent sending the request to the server.

    TCP Blocked (http_req_blocked-TCP)
        Time spent in the TCP connection phase.

    HTTP Request Connecting (http_req_connecting)
        Time spent establishing a TCP connection.

    TLS Handshaking (http_req_tls_handshaking)
        Time spent performing TLS handshakes (if applicable).

Data Source Configuration

    K6 Output to InfluxDB
    The dashboard retrieves data from InfluxDB, which is configured as the output for K6. Ensure the following is included in your K6 script or configuration file:

    k6 run --out influxdb=http://<INFLUXDB_HOST>:8086/<DATABASE_NAME> <SCRIPT.js>

    Replace:
        <INFLUXDB_HOST> with your InfluxDB host URL.
        <DATABASE_NAME> with the InfluxDB database name.

    Grafana Datasource
        In Grafana, configure an InfluxDB datasource pointing to the same database used by K6.

Dashboard Panels

Each metric is visualized in a dedicated panel:

    Time-series graphs for metrics like http_req_duration, http_req_waiting, and http_req_receiving provide percentile views (e.g., P90, P95) to analyze distribution.
    Counters such as errors and http_reqs provide cumulative totals.
    Gauges for metrics like vus and vus_max show real-time values.

