# Welcome to the Streaming Data 101!
This is meant to be a recipe for running streaming pipelines in Python.

## What's going on?
Subscribe to a pubsub topic, extract data and store in a BigQuery Table.

## What you'll need
```
- Python 2.7
- Apache Beam
- GCP Project
- Dataflow and PubSub APIs Enabled
- Access to Bigquery
```

## Example
First clone this repo.
```
git clone https://github.com/meirelon/streaming_data.git
cd streaming_data
```

Next, create a virtual environment with Python27 and install the apache beam dependency.
```
virtualenv py27 --python=/usr/bin/pyton2.7
source activate py27
pip install -r requirements.txt
```

Then create a new bucket for streaming logs.
```
gsutil mb gs://[PROJECT ID]-streaming
```

Create a folder within this bucket called `tmp` which will be used later in the process.

For this example, we are going to use the NYC Taxi Rides pubsub topic provided by GCP.
Now we deploy!
The command is going to look like the following:
```
python -m example --runner DataflowRunner --project [PROJECT ID] --temp_location gs://[PROJECT ID]-streaming/tmp/ --input_topic "projects/pubsub-public-data/topics/taxirides-realtime" --output_table "[PROJECT ID]:[DATASET NAME].[TABLE NAME]" --streaming
```

## Resources
More information about subscribing to the NYC Taxi Rides pubsub [here](https://github.com/googlecodelabs/cloud-dataflow-nyc-taxi-tycoon).
Please read about how pubsub works [here](https://cloud.google.com/pubsub/docs/overview).


## Contribute
I am happy to review [PRs](https://help.github.com/articles/about-pull-requests/), or if you liked this example, I also gladly accept [Crypto Currency](https://commerce.coinbase.com/checkout/1efcc118-420e-4512-b1f1-713b20c0f09e)!
