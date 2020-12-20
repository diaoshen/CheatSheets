#### Location of Yarn Global Packages

```
%LOCALAPPDATA%\Yarn\config\global
```

#### Create package.json

```
yarn init -y  //Accept all default
yarn init
```

#### Install a package

```
yarn add XXX
```

#### Create command

```
yarn create-react-app foo
```

#### Install stuff listed in package.json

```
yarn install
```

#### Remove a package

```
yarn remove XXX
```

#### Run scripts named : dev

```
yarn run dev
```

#### Check outdated

```
yarn outdated
yarn outdated XXX
```

#### Upgrade

```
yarn upgrade XXX
```

#### List package shows all dependency

```
yarn list
```

#### List package with depth

```
yarn list --depth=0
```

#### Check dependency for certain package

```
yarn list --pattern XXX
```

#### Add package as a development dependency

```
yarn add XXX --dev
```

#### Check if package.json matches yarn.lock

```
yarn check
```

#### Clean cache

```
yarn cache clean
```

#### Generate yarn.lock

```
yarn import
```
