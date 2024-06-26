在使用 npm（Node Package Manager）时，您可以查看和设置 npm 代理。代理通常用于在访问 npm registry 时提供网络访问。以下是查看和设置 npm 代理的一些方法：

### 查看 npm 代理：

1. **查看当前 npm 配置：**
   使用以下命令查看 npm 的当前配置，包括代理信息：
   ```bash
   npm config list
   ```

2. **查看代理设置：**
   ```bash
   npm config get proxy
   npm config get https-proxy
   ```

### 设置 npm 代理：

1. **设置代理：**
   ```bash
   npm config set proxy http://your-proxy-url:your-proxy-port
   npm config set https-proxy http://your-proxy-url:your-proxy-port
   ```

   替换 `your-proxy-url` 和 `your-proxy-port` 为您代理服务器的实际地址和端口。

2. **如果您使用的是 npm 的版本 5.7.0 及以上，您还可以使用以下命令：**
   ```bash
   npm config set proxy http://your-proxy-url:your-proxy-port --global
   npm config set https-proxy http://your-proxy-url:your-proxy-port --global
   ```

   这将在全局范围内设置代理，而不仅仅是当前项目。

3. **如果您的代理需要身份验证：**
   ```bash
   npm config set proxy http://username:password@your-proxy-url:your-proxy-port
   npm config set https-proxy http://username:password@your-proxy-url:your-proxy-port
   ```

   替换 `username`、`password`、`your-proxy-url` 和 `your-proxy-port` 为您代理服务器的实际信息。

4. **如果需要使用代理服务器来访问 https registry：**
   ```bash
   npm config set registry https://registry.npmjs.org/
   ```

   这将确保 npm 使用 https registry，并且您可以设置 https 代理。

请注意：在设置代理时，请根据您所在的网络环境和代理服务器的配置进行相应的设置。
如果您想从 npm 配置中移除代理，可以使用以下命令：

### 移除 HTTP 代理：

```bash
npm config delete proxy
```

### 移除 HTTPS 代理：

```bash
npm config delete https-proxy
```

### 移除 registry 代理：

```bash
npm config delete registry
```

这将删除相应的配置项，从而取消代理设置。请确保您的 npm 配置不再包含不必要的代理信息。如果之前设置了全局代理，可以使用 `--global` 标志删除全局代理配置：

```bash
npm config delete proxy --global
npm config delete https-proxy --global
```

请注意，这些命令会将相应的配置项从您的 npm 配置文件中删除，而不是将它们设置为空。确保在不再需要代理的情况下使用这些命令。

# npm 替换源
这是 npm 默认的源
`npm config set registry https://registry.npmjs.org/`
