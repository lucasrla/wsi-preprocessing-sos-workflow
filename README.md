# wsi-preprocessing-sos-workflow

A simple pipeline built with [SoS Workflow](https://vatlab.github.io/sos-docs/workflow.html) that runs [wsi-preprocessing](https://github.com/lucasrla/wsi-preprocessing) on a remote machine.

[wsi-preprocessing](https://github.com/lucasrla/wsi-preprocessing) is a simple library for preprocessing histopathological whole-slide images (WSI) towards deep learning. Check out its [repository](https://github.com/lucasrla/wsi-preprocessing).

If you do not have a remote machine ready, you can launch a new AWS EC2 instance with [ec2-setup-sos-workflow](https://github.com/lucasrla/ec2-setup-sos-workflow).


## Installation

### conda

```sh
conda create --name YOUR_ENV_NAME --channel conda-forge python=3.6 pyyaml boto3 sos black
# black is optional, it is sort of a development dependency

git clone https://github.com/lucasrla/wsi-preprocessing-sos-workflow

cd wsi-preprocessing-sos-workflow

conda activate YOUR_ENV_NAME
```

### poetry or pip

```sh
git clone https://github.com/lucasrla/wsi-preprocessing-sos-workflow

cd wsi-preprocessing-sos-workflow

# create and activate a virtualenv, for example:
pyenv virtualenv YOUR_ENV_NAME && pyenv local YOUR_ENV_NAME

# install the dependencies, either with:
poetry install
# or:
pip install -r requirements.txt

# note, requirements.txt in this repository were generated via:
# poetry export --without-hashes -f requirements.txt -o requirements.txt
```


## Configuration

```sh
# edit project.TEMPLATE.yml to match your needs
vim project.TEMPLATE.yml
# and then save it as project.yml

# make sure that ~/.sos/hosts.yml has the path to your pem_file 
# and that the naming of hosts matches project.yml
vim ~/.sos/hosts.yml
```


## Usage

```sh
sos run -c project.yml remote.sos -v4
```

For more tips and tricks on SoS, read the [official docs](https://vatlab.github.io/sos-docs/workflow.html). 

You can also have a look at [ec2-setup-sos-workflow](https://github.com/lucasrla/ec2-setup-sos-workflow).


## License

This is [Free Software](https://www.gnu.org/philosophy/free-sw.html) distributed under the [GNU General Public License v3.0](https://choosealicense.com/licenses/gpl-3.0/).