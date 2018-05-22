#### S2I Python 3.5
Project that modify a environmente of S2I python container. The original and credits are https://github.com/sclorg/s2i-python-container.git

The only alteration is the possible change of requirements.txt file.

``` bash
if [ ${ENV_REQ}x != 'x' ]; then
  REQUIREMENTS=${ENV_REQ}
else
  REQUIREMENTS=requirements.txt  
fi  

if [[ ! -z "$ENABLE_PIPENV" ]]; then
  install_pipenv
  echo "---> Installing dependencies via pipenv ..."
  if [[ -f Pipfile ]]; then
    pipenv install --deploy
  elif [[ -f $REQUIREMENTS ]]; then
    pipenv install -r $REQUIREMENTS 
  fi
  # pipenv check
elif [[ -f $REQUIREMENTS ]]; then
  echo "---> Installing dependencies ..."
  pip install -r $REQUIREMENTS
fi
```

