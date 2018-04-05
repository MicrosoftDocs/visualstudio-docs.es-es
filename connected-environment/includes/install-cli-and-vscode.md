## <a name="install-the-connected-environment-cli"></a>Instalar la CLI de Connected Environment
Connected Environment requiere una configuración mínima del equipo local. La mayor parte de la configuración del entorno de desarrollo se almacena en la nube y se puede compartir con otros usuarios.

### <a name="install-on-mac"></a>Instalar en Mac
Descargue e instale la CLI de Connected Environment:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Instalar en Windows
1. Instale [Git para Windows](https://git-scm.com/downloads) seleccionando las opciones de instalación predeterminadas. 
1. Descargue **kubectl.exe** desde [este vínculo](https://storage.googleapis.com/kubernetes-release/release/v1.9.0/bin/windows/amd64/kubectl.exe) y **guárdelo** en una ubicación de su ruta de acceso.
1. Descargue y ejecute el [instalador de la CLI de Connected Environment](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Instalar en Linux
Próximamente...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Obtener la depuración de Kubernetes para VS Code
Aunque la CLI de Connected Environment se puede usar como una herramienta independiente, los desarrolladores de .NET Core y Node.js que usen VS Code tienen a su disposición algunas características sofisticadas, como la depuración de Kubernetes.

1. Si no la tiene, instale [VS Code](https://code.visualstudio.com/Download).
1. Descargue la [extensión de VS Connected Environment](https://aka.ms/get-vsce-code).
1. Instale la extensión: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.0.vsix
```
