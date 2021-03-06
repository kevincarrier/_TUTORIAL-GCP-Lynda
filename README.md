# Google Cloud Platform Course on Lynda
Lynda Course: https://www.lynda.com/Google-Cloud-Platform-tutorials/Google-Cloud-Platform-Essential-Training/540539-2.html

Google Cloud Tools: https://cloud.google.com/docs/overview/developer-and-admin-tools

## Install Cloud SDK
<ol>
  <li>Go to https://cloud.google.com/sdk/docs/ and install the latest version of Cloud SDK.</li>
  <li>If you do not have a version of Python 2 that is 2.7.9 or later install Python 2.</li>
  <li>Once completely installed a gcloud init command will be run and you will need to sign in with your google account</li>
  <li>Some useful gcloud commands
    <ul>
      <li>gcloud init <my-project></li>
      <li>gcloud --version</li>
      <li>gcloud info --show-log</li>
      <li>gcloud auth login</li>
      <li>gcloud config set project <my-project-id></li>
    </ul>
  </li>
</ol>

## Google Compute Engine
<i><a href="https://cloud.google.com/compute/">Compute Engine</a> is a cloud-hosted virtual machine</i>
<ol>
  <li>In the Compute Section of the console select Compute Engine and then Create</li>
  <li>Keep all defaults and then create</li>
  <li>Once set up connect via SSH by selecting the Open in Browser Window in the Connect column</li>
  <li>Setup a snapshot by selecting snapsnot and then selecting the instance.</li>
</ol>
<i><a href="https://cloud.google.com/marketplace/">Cloud Launcher/Marketplace</a> is a preconfigured cloud-hosted virtual machine with applications</i>
<ol>
  <li>Select Marketplace and then select WordPress</li>
  <li>Select Launch on Compute Engine</li>
  <li>Keep defaults and Deploy</li>
  <li>Now you can view the Wordpress Public and Admin Page</li>
</ol>

## Google Kubernetes Container Engine
<i><a href="https://cloud.google.com/kubernetes-engine/">Kubernetes Engine</a> is a managed, production-ready environment for deploying containerized applications.</i>
<ol>
  <li>In the Compute Section of the console select Kubernetes Engine and then Create</li>
  <li>Keep all defaults and then create</li>
  <li>Follow the Create a Guestbook with Redis and PHP tutorial
    <ul>
      <li>In the gcloud console in the browser clone the <a href="https://github.com/kubernetes/examples">Kubernetes Repo</a> and cd into guestbook</li>
        <li>Setup gcloud and kubernetes credentials
          <pre>
          <code>
          gcloud container clusters \
          get-credentials <cluster-name> \
          --zone <cluster-zone>
          </code>
          </pre>
        </li>
        <li>Deploy the master controller
          <pre>
          <code>
          kubectl create -f \
          redis-master-deployment.yaml
          </pre>
          </code>
        </li>
        <li>Verify the redis master pod is running
          <pre>
          <code>
          kubectl get pods 
          </pre>
          </code>
        </li>
        <li>Create the redis master service
          <pre>
          <code>
          kubectl create -f \
          redis-master-service.yaml
          </pre>
          </code>
        </li>
        <li>Verify the service created successfully
          <pre>
          <code>
          kubectl get service
          </pre>
          </code>
        </li>
        <li>Deploy a slave controller
          <pre>
          <code>
          kubectl create -f \
          redis-slave-deployment.yaml
          </pre>
          </code>
        </li>
        <li>Create the redis salve service
          <pre>
          <code>
          kubectl create -f \
          redis-slave-service.yaml
          </pre>
          </code>
        </li>
        <li>Verify the service created successfully
          <pre>
          <code>
          kubectl get service
          </pre>
          </code>
        </li>
        <li>Create the guestbook frontend
        <pre>
          <code>
          kubectl create -f \
          frontend-deployment.yaml;
          <br/>
          sed -i -e 's/NodePort/LoadBalancer/g' \
          frontend-service.yaml;
          <br/>
          kubectl create -f \
          frontend-service.yaml;
          </pre>
          </code>
        </li>
        <li>List all fo the services and look for the front end. Wait for it to go an extranl IP and then visit the running site.
        kubectl get services --watch
        </li>
      </li> 
    </ul>
  </li>
</ol>

## Google App Engine
<i><a href="https://cloud.google.com/appengine/">App Engine</a> is a powerful platform to build apps and scale automatically.</i>
<ol>
  <li>In the Compute Section of the console select App Engine and then select your language (example Python)</li>
  <li>Select region</li>
  <li>Follow the App Engine Quick Start tutorial (Python)
    <ul>
      <li>In the gcloud console in the browser clone the <a href="https://github.com/GoogleCloudPlatform/python-docs-samples">Python GCP Repo</a> and cd into python-docs-samples/appengine/standard_python37/hello_world</li>
      <li>Create an isolated Python environment to test
          <pre>
          <code>
          virtualenv --python python3 \
          ~/envs/hello_world
          </pre>
          </code>
      </li>
      <li>Activate the new virtual environment
        <pre>
        <code>
        source \
        ~/envs/hello_world/bin/activate
        </code>
        </pre>
      </li>
      <li> Pip install all dependencies
        <pre>
        <code>
        pip install -r requirements.txt
        </code>
        </pre>
      </li>
      <li> Run app using Flask development server
        <pre>
        <code>
        python main.py
        </code>
        </pre>
      </li>
      <li>Deploy App
        <pre>
        <code>
        gcloud app deploy app.yaml --project \
        gcp-lynda-course
        </code>
        </pre>
      </li>
      <li>Note for multiple services add service : <service name> to app.yaml file for Python or <service>service name</service> to appengine-web.xml for Java</li> 
    </ul>
  </li>
</ol>

## Google Cloud Storage
<i><a href="https://cloud.google.com/storage/">Cloud Storage</a> is a unified object storage for developers and enterprises</i>
<ol>
  <li>In the Storage Section of the console select Storage</li>
  <li>Click create bucket and set a storage class</li>
  <li>Test with <a href="https://developers.google.com/apis-explorer/#p/storage/v1/">Cloud Storage JSON API Explorer</a></li>
</ol>

## Google Cloud SQL
<i><a href="https://cloud.google.com/sql/">Cloud SQL</a> is a fully-managed database service that makes it easy to set up, maintain, manage, and administer your relational PostgreSQL and MySQL databases in the cloud</i>
<ol>
  <li>In the Storage Section of the console select SQL</li>
  <li>Create instance and select either MySQL or PostgreSQL</li>
  <li>Select 2nd Generation (Recommended) or 1st Generation (Legacy)</li>
  <li>Set Instance ID and password and then create</li>
</ol>

## Google Cloud Datastore
<i><a href="https://cloud.google.com/datastore/">Cloud Datastore</a> is a highly-scalable NoSQL database for your web and mobile applications</i>
<ol>
  <li>In the Storage Section of the console select Datastore</li>
  <li>Create an entity set kind to "Task" and add 3 properties description (string), created (date), doen (boolean)</li>
</ol>

## Google Cloud Bigtable
<i><a href="https://cloud.google.com/bigtable/">Cloud Bigtable</a> is a petabyte-scale, fully managed NoSQL database service for large analytical and operational workloads.</i>
<ol>
  <li>In the Storage Section of the console select Bigtable</li>
  <li>Create an instance by entering the instance name, selecting the region, and keeping the rest of the defaults.</li>
</ol>

## Google BigQuery
<i><a href="https://cloud.google.com/bigquery/">BigQuery</a> is a fast, highly scalable, cost-effective, and fully managed cloud data warehouse for analytics, with built-in machine learning.</i>
<ol>
  <li>In the Big Data Section of the console select BigQuery</li>
  <li>Follow the <a href="https://cloud.google.com/bigquery/docs/quickstarts/quickstart-web-ui">Quickstart Using the BigQuery Web UI</a>
    <ul>
      <li>Open <a href="https://console.cloud.google.com/bigquery?p=bigquery-public-data&page=project">this url</a> and pin the bigquery-public-data</li>
      <li>Copy the query below and then run query
        <pre>
        <code>
        SELECT
          name, gender,
          SUM(number) AS total
        FROM
          `bigquery-public-data.usa_names.usa_1910_2013`
        GROUP BY
          name, gender
        ORDER BY
          total DESC
        LIMIT
          10
        </code>
        </pre>
      </li>
      <li>Create a new dataset and set the id to babynames</li>
      <li>Create table and set create table from upload, select yob_2014.txt (file downloaded from quickstart), change file format to CSV, make table name names_2014, and in the schema enable edit as text and add the following and then create table
        <pre>
        <code>
        name:string,gender:string,count:integer
        </code>
        </pre>
      </li>
      <li>You can preview the data in the preview tab</li>
      <li>Run the following query
        <pre>
        <code>
        SELECT
         name, count
        FROM
         `babynames.names_2014`
        WHERE
         gender = 'M'
        ORDER BY count DESC LIMIT 5
        </code>
        </pre>
      </li>
    </ul>
  </li>
</ol>

## Pub Sub
<i><a href="https://cloud.google.com/pubsub/docs/overview">Pub Sub</a> brings the scalability, flexibility, and reliability of enterprise message-oriented middleware to the cloud.</i>
<ol>
  <li>In the Big Data Section of the console select Pub Sub</li>
  <li>Create a topic with the following gcloud command
    <pre>
    <code>
    gcloud pubsub topics create my-topic
    </code>
    </pre>
  </li>
  <li>Create a subscription with the following gcloud command
    <pre>
    <code>
    gcloud pubsub subscriptions \
    create my-sub --topic my-topic \
    --ack-deadline=60
    </code>
    </pre>
  </li>
  <li>Publish messages to the topic using the following gcloud command
    <pre>
    <code>
    gcloud pubsub topics publish my-topic \
    --message hello
    gcloud pubsub topics publish my-topic \
    --message goodbye
    </code>
    </pre>
  </li>
  <li>Pull messages from subscription using the following gcloud command
    <pre>
    <code>
    gcloud pubsub subscriptions \
    pull --auto-ack --limit=2 my-sub
    </code>
    </pre>
  </li>
</ol>

## Google Cloud Vision API
<i><a href="https://cloud.google.com/vision/">Cloud Vision</a> derives insight from your images with our powerful pretrained API models or easily train custom vision models with AutoML Vision.</i>
<ol>
  <li>In the Artifical Intelligence Section of the console select Vision</li>
  <li>Follow the Cloud Vision Quick Start Tutorial
    <ul>
      <li>In the gcloud console in the browser clone the <a href="https://github.com/GoogleCloudPlatform/python-docs-samples">Python GCP Repo</a> and cd into python-docs-samples/vision/cloud-client/quickstart</li>
      <li>Create a service account
        <pre>
        <code>
        gcloud iam service-accounts create \
        vision-quickstart --project \
        gcp-lynda-course;
        <br/>
        gcloud iam service-accounts keys \
        create key.json --iam-account \
        vision-quickstart@gcp-lynda-course.iam.gserviceaccount.com;
        <br/>
        export \
        GOOGLE_APPLICATION_CREDENTIALS=key.json;
        </code>
        </pre>
      </li>
      <li>Run with a python quickstart.py command</li>
    </ul>
  </li>
</ol>
