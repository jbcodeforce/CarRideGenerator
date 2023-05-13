# Autonomous Car Ride Generator

Python Lambda function to read pre-defined car ride for autonomous cars and send them to destination, which is configured by CDK.

## Requirements

* [ ] Read car rides from csv file from S3
* [ ] Expose API in API Gateway for `/simul` POST with following payload: 

    ```json
    {"timestamp" : "",
     "command": "one of start, stop",
     "type" : "one of random, predefined",
     "nbOfRecords": 100
    }
    ```
* [ ] Generate events to streaming platform: Kinesis Data Streams or MSK

## How it was created

Using SAM and python Lambda powertools:

```sh
sam init --app-template hello-world-powertools-python --name carridegenerator --package-type Zip --runtime python3.10 --no-tracing
```

Unit test it

```sh
curl -X POST http://localhost:8080/simul -H 'Content-type: application/json' -d @events/unittestevent.json
```


## Resources

* [Python Lambda powertools](https://awslabs.github.io/aws-lambda-powertools-python/2.15.0/tutorial/)