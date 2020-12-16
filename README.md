# IGF Dockerfiles
A list of dockerfiles for Docker and singularity image building

## Build Docker image

<pre><code>
cd TOOL_DIR

docker build -t TOOL_NAME:v_VERSION .
</code></pre>

## Build Singularity image

<pre><code>
cd TOOL_DIR

docker build -t TOOL_NAME:v_VERSION .

singularity build TOOL_NAME_v_VERSION.sif docker-daemon://TOOL_NAME:v_VERSION
</code></pre>
