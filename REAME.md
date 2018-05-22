#### S2I Python 3.5

Copia do projeto sclorg/s2i-python-container. A única alteração é a possibilidade de especificação do requirementes.txt
``` bash
if [ -z "${ENV_REQ}" ]; then
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
