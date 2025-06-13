# Unity ML-Agents Python Interface

The `mlagents_envs` Python package is part of the
[ML-Agents Toolkit](https://github.com/Unity-Technologies/ml-agents).
`mlagents_envs` provides three Python APIs that allows direct interaction with the
Unity game engine:
- A single agent API (Gym API)
- A gym-like multi-agent API (PettingZoo API)
- A low-level API (LLAPI)

The LLAPI is used by the trainer implementation in `mlagents`.
`mlagents_envs` can be used independently of `mlagents` for Python
communication.

## Usage & More Information

See
- [Gym API Guide](../docs/Python-Gym-API.md)
- [PettingZoo API Guide](../docs/Python-PettingZoo-API.md)
- [Python API Guide](../docs/Python-LLAPI.md)

for more information on how to use the API to interact with a Unity environment.

For more information on the ML-Agents Toolkit and how to instrument a Unity
scene with the ML-Agents SDK, check out the main
[ML-Agents Toolkit documentation](../docs/Readme.md).

## Limitations

- `mlagents_envs` uses localhost ports to exchange data between Unity and
  Python. As such, multiple instances can have their ports collide, leading to
  errors. Make sure to use a different port if you are using multiple instances
  of `UnityEnvironment`.
- Communication between Unity and the Python `UnityEnvironment` is not secure.
- On Linux, ports are not released immediately after the communication closes.
  As such, you cannot reuse ports right after closing a `UnityEnvironment`.

## Development and publishing (Wargaming artifactory)

Since this package does not seem to be maintained anymore be the official developers, we have forked it to the Wargaming gitlab and are maintaining it there.
Publishing is done via the [Wargaming artifactory](https://ed.artifactory.wgdp.io:443/artifactory/api/pypi/mlopsbi-pypi/simple).

To contribute to the `mlagents_envs` package, please work on a branch and create a merge request to `master` once ready.
Once the merge request is approved and merged to `master` branch, a gitlab pipeline will automatically create a new git tag and publish the new version to the Wargaming artifactory.

## Installation (Wargaming artifactory)

Since publishing is done via the Wargaming artifactory, you can use this package as dependency by adding the following to your `pyproject.toml`:

```toml
[tool.poetry.dependencies]
mlagents-envs = { version = "^0.1", source = "artifactory" }

[[tool.poetry.source]]
name = "artifactory"
url = "https://ed.artifactory.wgdp.io:443/artifactory/api/pypi/mlopsbi-pypi/simple"
priority = "explicit"
```


Or you can install the `mlagents_envs` package from the Wargaming artifactory using pip:

```bash
pip install mlagents-envs --extra-index-url https://ed.artifactory.wgdp.io:443/artifactory/api/pypi/mlopsbi-pypi/simple
```
