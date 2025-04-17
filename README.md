# functions-from-zero-mlops2

## Configure Development Environment

- Create devcontainer (shift+cmd+p)
- Add Extensions
- touch Makefile + requirements.txt
```bash
install:
	pip install --upgrade pip
	pip install -r requirements.txt

test:
	python -m pytest -vv --cov=Project test_*.py

format:
	black *.py

lint:
	pylint --disable=R,C --ignore-pattern=test_*.py *.py

refactor: format lint

deploy:
	echo "Deploying to production..."
	# Add your deployment commands here

all: install lint test format deploy
```
```
pytest
pytest-cov
pylint
black
fire
fastapi
uvicorn[standard]
pydantic
boto3
...
```

- Create virtual environment: `python -m venv .venv`

- Aws configs
`mkdir ~/.aws`
`vim ~/.aws/credentials`
```bash
[default]
aws_access_key_id = YOUR_KEY
aws_secret_access_key = YOUR_SECRET
```

`vim ~/.aws/config`
```bash
[default]
region=us-east-1
```

## Interactive debugging

```python
import ipdb
ipdb.set_trace()
```