# qgis_geonode

A QGIS plugin that provides integration with GeoNode

## Development

This plugin uses [poetry] and [typer].

- Fork the code repository
- Clone your fork locally
- Install poetry
- Install the plugin dependencies into a new virtual env with
  
  ```
  cd qgis_geonode
  poetry install
  ```

- The plugin comes with a `pluginadmin.py` python module, which provides a nice CLI 
  with commands useful for development:
  
  ```
  poetry run python pluginadmin --help
  poetry run python pluginadmin install
  ```
  
- When testing out the plugin locally you just need to call 
  `poetry run python pluginadmin.py install`. Alternatively, the [plugin reloader] QGIS 
  plugin can be used as a means to install and reload the plugin. The functionality 
  that allows re-running the poetry install command is currently in a [proposed] state, 
  so you may install plugin reloader directly from the github fork mentioned in the 
  above pull request
  

## Running tests

Tests are made with [pytest] and [pytest-qt]. They can be ran with:

```
export COMPILED_QGIS_PATH=$HOME/dev/QGIS/build_master/build-QGIS-QGIS_Build-Debug/output
poetry run pytest --verbose -k apiclient --ignore-glob="test/test_[iqQrt]*"
```

NOTE: The previous incantation seems a bit funky because we have not removed the 
default tests that are generated by the plugin builder yet. These confuse pytest, 
which tries to run all files starting with `test_` by default


[poetry]: https://python-poetry.org/
[typer]: https://typer.tiangolo.com/
[plugin reloader]: https://github.com/borysiasty/plugin_reloader
[proposed]: https://github.com/borysiasty/plugin_reloader/pull/22
[pytest]: https://docs.pytest.org/en/latest/
[pytest-qt]: https://github.com/pytest-dev/pytest-qt
