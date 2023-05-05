# Builtin Fixtures

## `monkeypatch`
1. `monkeypatch`: Dynamic modification of a class or module during runtime.
2. Replacing either input dependencies or output dependencies with objects or functions that are more convenient for testing.
3. `monkeypatch` has following functions :
   - `setattr(target, name, value, raising=True)`: Sets an attribute
   - `delattr(target, name, raising=True)`: Deletes an attribute
   - `setitem(dic, name, value)`: Sets a dictionary entry
   - `delitem(dic, name, raising=True)`: Deletes a dictionary entry
   - `setenv(name, value, prepend=None)`: Sets an environment variable
   - `delenv(name, raising=True)`: Deletes an environment variable
   - `syspath_prepend(path)`: Prepends path to `sys.path`, which is Python’s list of import locations
   - `chdir(path)`: Changes the current working directory
