# Week 2 — Distributed Tracing

## Tasks to Complete
- [**MY NOTES**](#my-notes)<br>
  ✅ [Distributed Tracing](#distributed-tracing)<br>
  ✅ [Instrument XRay](#instrument-xray)<br>
  ✅ [CloudWatch Logs](#cloudwatch-logs)<br>
  ✅ [Observability Security Consideration](#observability-security-considerations)<br>
  ✅ [Observabilithy Spending Considerations](#observability-spending-considerations)<br>
## MY NOTES
### Distributed Tracing
 - AWS Xray is same as honeycomb. But honeycomb is easier
 - application to be instrumented 
   - login to honeycomb [ui.honeycomb.io]
   - environemnt  is like dev, production. Create one for bootcamp
   - API creates u create determine which environment u land in
   - Set the API key 
   ```sh
   gp env HONEYCOMB_API_KEY="JpMuOqYDv4hJRJiTm8TaBB"
   ```
   check with 
   ```sh
   env | grep honeycomb
   ```
   -Set Service name
   ```sh
   export HONEYCOMB_SERVICE_NAME="Cruddur"
   gp env HONEYCOMB_SERVICE_NAME="Cruddur"
   ```
   or this can be set in docker-compose file to specifically mention a service name for each part of the project in environemnt
   ```sh
   OTEL_SERVIVCE_NAME:"backend-flask"
   ```
   OTEL - CNCF - Open telemetry - standard for observing 
   add the following code in environment in docker-compose file
    ```sh
    OTEL_EXPORTER_OTLP_ENDPOINT: "https://api.honeycomb.io"
    OTEL_EXPORTER_OTLP_HEADERS: "x-honeycomb-team=${HONEYCOMB_API_KEY}"
    ```
   Instructions for Python with Flask code [https://ui.honeycomb.io/project.awscloud-gettingstarted/environments/bootcamp/send-data#]
   place the following code in requirements.txt
    ```sh
    opentelemetry-api 
    opentelemetry-sdk 
    opentelemetry-exporter-otlp-proto-http 
    opentelemetry-instrumentation-flask 
    opentelemetry-instrumentation-requests
    ```
  
   Run pip instal in gitpod /backend-flask dir
    ```sh
    pip install -r requirements.txt
    ```
   Add the following code in app.py and add comment 
    ```sh
    from opentelemetry import trace
    from opentelemetry.instrumentation.flask import FlaskInstrumentor
    from opentelemetry.instrumentation.requests import RequestsInstrumentor
    from opentelemetry.exporter.otlp.proto.http.trace_exporter import OTLPSpanExporter
    from opentelemetry.sdk.trace import TracerProvider
    from opentelemetry.sdk.trace.export import BatchSpanProcessor
    ```
  
   place this code above app = Flask(__name__)
    ```sh
    # Initialize tracing and an exporter that can send data to Honeycomb
    provider = TracerProvider()
    processor = BatchSpanProcessor(OTLPSpanExporter())
    provider.add_span_processor(processor)
    trace.set_tracer_provider(provider)
    tracer = trace.get_tracer(__name__)
     ```
     
   Add this code below app = Flask(__name__)
    ```sh
    # Initialize automatic instrumentation with Flask
    
    FlaskInstrumentor().instrument_app(app)
    RequestsInstrumentor().instrument()
    ```
   
    
  
### Instrument XRay

### Cloudwatch Logs

### Observability Security Consideration
#### Logging
Monolithic - Everythiong is in one place and tightly coupled
Microservices - 
Infra Logs
Application logs
Antivirus
Firewall

Instead of logging everything, log what is needed
Observability reduces alert fatigue, solving log problems
visibility of end2end logs
looking at holistic picture
#### Observability vs Monitoring
Observability - entire lifecycle of a program
Monitoring - looks at one specific application, does not look at third party services outside the application
Observabilioty 
  - Logs 
  - Traces - pinpoint the exact start of the problem
  - Metrics - to enhance the log produced and use certain techniques 

AWS Observability services
  - AWS CloudWatch `logs
  - AWS CloudWtach metrics
  - AWS X Ray traces

Instrumentation
what helps to produce logs or metrics


Send cloudtrail logs to cloudwatch and setup metrics in the log-groups


Applications (Which application & Type of application)--> 
      Threat Modelling (Identify Attack vectors)--> 
            Industry Known Attack/Techniques(Map attack vectors to TTP in Attack MITRE Framework) --> 
                  What agents available for Instrumentation (Tracing like Cloudwatch agents)-->
                          AWS Services like AWS DISTro for OTEL-->
                          Dashboard for practical attack vectors for that application -->
                                Repeat for next application
 
 
Central observability Platform - Security
  - AWS Security Hub with Eventbridge
  - SIEM
  - Open Source Dashboards
  - Event Driven Architecture with AWS Services
