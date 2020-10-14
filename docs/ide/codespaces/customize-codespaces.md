---
title: Personalización de un codespace (versión preliminar)
description: Más información sobre cómo personalizar un codespace.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 2223aecd66da721ff1afe9877853c8a00c837611
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862225"
---
# <a name="how-to-customize-a-codespace-preview"></a>Personalización de un codespace (versión preliminar)

GitHub Codespaces ofrece un entorno de desarrollo completo en la nube. Para el desarrollo basado en Windows con Visual Studio 2019, las instancias predeterminadas de GitHub Codespaces proporcionan un excelente punto de partida, pero también se puede personalizar el entorno para el proyecto específico.

## <a name="installed-software"></a>Software instalado

Los codespaces de Windows incluyen muchos marcos y herramientas ya instalados, por lo que puede comenzar de inmediato. En la tabla siguiente se enumeran las aplicaciones y características disponibles en todos los entornos de Windows Codespace.

| Aplicación                                         | Path Alias | Versión            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | N/D        | 4.8                |
| Runtime de .NET Core                           | dotnet     | 2.1, 3.1           |
| SDK de .NET Core                               | dotnet     | 2.1, 3.1.3, 3.1.4  |
| Azure CLI                                   | az         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3,17               |
| Git                                         | git        | 2.26               |
| Microsoft Build                             | msbuild    | 16.7               |
| Microsoft SQL Server Express Edition 2019   | N/D        | 15.0               |
| Ninja                                       | ninja      | 1.8.2              |
| Node.js                                     | Nodo       | 12.16              |
| NPM                                         | npm        | 6,14               |
| Python                                      | Python     | 3.7                |
| Administrador de paquetes VC                          | vcpkg      | 2020.02            |
| Windows SDK                                 | N/D        | 10.0.18362         |

La lista anterior no es exhaustiva y excluye muchas herramientas que Visual Studio instala (por ejemplo, IISExpress). Es posible que un componente pueda tener también una versión secundaria o de revisión distinta de la indicada anteriormente.

Los detalles específicos acerca de las herramientas y los marcos preinstalados se ofrecen en la sección correspondiente a los [detalles del software instalado](#installed-software-specifics) a continuación.

## <a name="modifications-to-a-codespace"></a>Modificaciones en un codespace
 
Una vez que se crea un codespace, se conservan los cambios realizados en ese codespace específico, mientras que la instancia de codespace está disponible en GitHub Codespaces. Puede clonar repositorios adicionales, instalar herramientas y generadores de aplicaciones y agregar otros recursos de desarrollo, y estas modificaciones se conservarán aunque el codespace se suspenda. Sin embargo, si elimina un codespace, las modificaciones desaparecerán.

> [!NOTE]
> Si elimina un codespace, cualquier cambio realizado en un repositorio local (pendiente o confirmado) del codespace se perderá. Asegúrese de enviar los cambios del repositorio a una ubicación remota antes de eliminar un codespace.

Mientras esté conectado a un codespace con Visual Studio, puede usar el terminal de Visual Studio para ejecutar herramientas de la línea de comandos. Puede usar PowerShell o el símbolo del sistema de Windows, ambos con privilegios en la cuenta de administrador local. Para saber más sobre el terminal de Visual Studio, consulte el [blog del anuncio del terminal de Visual Studio](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/).

## <a name="customize-a-codespace"></a>Personalización de un codespace

El valor real de GitHub Codespaces se produce cuando se pueden crear entornos de desarrollo únicos y repetibles en la nube adaptados a su propio trabajo y al de su equipo. Al compilar en una instancia predeterminada de GitHub Codespaces, puede personalizar lo que se instala y configura al crear un codespace.

En las secciones siguientes se describen dos métodos de configuración de codespace que usan los archivos *.devcontainer.json* y *.devinit.json*. Estos archivos permiten configurar los marcos y las herramientas de instalación para un codespace y, cuando se agregan al repositorio, cualquier persona que cree un codespace basado en el repositorio tendrá el mismo entorno de desarrollo remoto.

## <a name="customize-with-devcontainerjson"></a>Personalización con devcontainer.json

Cuando se crea un codespace, GitHub Codespaces busca un archivo [*devcontainers.json*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) en la raíz del repositorio y usa la configuración incluida para personalizar las instancias de codespace o de cliente que se conectan a él (editor del explorador base, Visual Studio o Visual Studio Code). La mayor parte de la configuración de *devcontainer.jason* se aplica a codespaces basados en Linux o a los otros dos clientes, pero algunos están disponibles para los codespaces de Windows y Visual Studio.

El archivo *devcontainer.json* puede colocarse en uno de los dos lugares de un repositorio:

1. *{repository-root}/.devcontainer.json*
2. *{repository-root}/.devcontainer/devcontainer.json*

GitHub Codespaces admite las siguientes propiedades de *devcontainer.json*. La configuración de propiedades específicas de Visual Studio Code resulta útil si espera conectarse a su codespace con los demás clientes además de Visual Studio. 

* `extensions`: matriz de extensiones de [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) que debe instalarse.
* `settings`: conjunto de [valores de Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings) que se va a aplicar.
* `forwardPorts`: puerto o matriz de puertos que se deben reenviar localmente de forma automática cuando se ejecuta el codespace.
* `postCreateCommand`: cadena de comandos o lista de argumentos de comando que se ejecutarán después de la creación del codespace.

> [!NOTE]
> Los archivos **devcontainer.json** también se usan para admitir [Desarrollo remoto](https://code.visualstudio.com/docs/remote/remote-overview) de Visual Studio Code, e incluyen propiedades adicionales que no se abordan en este documento. Estas propiedades adicionales se pueden agregar al archivo de forma segura, pero Codespaces las omitirá. Para más información, consulte la [referencia de devcontainer.json](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) en code.visualstudio.com.

## <a name="customize-with-devinit"></a>Personalización con devinit

[devinit](../../devinit/getting-started-with-devinit.md) es una herramienta de la línea de comandos incluida en los codespaces de Windows que permite instalar marcos y herramientas en el entorno. Se puede ejecutar manualmente desde un símbolo del sistema (`devinit -t require-dotnetcoresdk`), pero su eficacia real procede de la creación de un archivo [ *.devinit.json*](../../devinit/devinit-json.md) personalizado para configurar de forma uniforme un codespace cada vez que cree uno.

`devinit` incluye un conjunto de herramientas para instalar elementos concretos como, por ejemplo, SQL Server y la CLI de Azure, y también ejecutar administradores de paquetes generales tales como Chocolatey, npm y vcpkg. Puede encontrar la lista completa de herramientas de `devinit` en la documentación de [Herramientas disponibles](../../devinit/devinit-tool-list.md).

### <a name="devinitjson"></a>devinit.json

Aunque puede ejecutar la línea de comandos de `devinit` directamente, se recomienda crear archivos de configuración [*devinit.json*](../../devinit/devinit-json.md), que describen el conjunto de herramientas de `devinit` que se ejecutarán. 

Por ejemplo, para instalar el [SDK de .NET Core](/dotnet/core/sdk), un archivo *.devinit.json* sería similar al siguiente:

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

Cuando cree un archivo *.devinit.json* en la raíz del proyecto, se usará cuando se ejecute `devinit init`. De forma predeterminada, `devinit.exe` busca el archivo en las siguientes ubicaciones:

1. *{current-directory}\\.devinit.json*
2. *{current-directory}\\.devinit\devinit.json*

### <a name="running-devinit-when-creating-a-codespace"></a>Ejecución de devinit al crear un codespace

Puede indicar a GitHub Codespaces que ejecute `devinit` después de que se cree un codespace mediante la propiedad `postCreateCommand` en un archivo *devcontainers.json*. Como se mencionó anteriormente, GitHub Codespaces buscará un archivo *devcontainer.json* en el repositorio clonado para personalizar la instancia de codespace o de cliente, y ejecutará los comandos descritos en la propiedad `postCreateCommand`.

Al especificar `devinit init`, `devinit` se ejecutará con la configuración *devinit.json*.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>Un ejemplo

A continuación se muestra un ejemplo sencillo de instalación de la herramienta de línea de comandos de Entity Framework de .NET Core, `dotnet-ef`.

**devcontainer.json**

Contenido del archivo *devcontainer.json* en la raíz del repositorio. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.json**

Contenido del archivo *devinit.json*. Este archivo debe estar en la misma carpeta que *.devcontainer.json*.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

Puede encontrar más ejemplos de `devinit` en la [lista de ejemplos](../../devinit/sample-readme.md) de `devinit`.

## <a name="port-forwarding"></a>Reenvío de puertos

GitHub Codespaces proporciona acceso a las aplicaciones y los servicios que se ejecutan en los entornos remotos mediante el reenvío de puertos. De forma predeterminada, no se reenvía ningún puerto por cuestiones de seguridad. Sin embargo, se puede especificar que determinados puertos se abran en un codespace.

### <a name="configure-port-forwarding"></a>Configuración del reenvío de puertos

Si hay uno o más puertos que deben reenviarse de forma predeterminada para un repositorio determinado, eso se puede configurar en *devcontainer.json* con la propiedad `forwardPorts`.

* `forwardPorts`: puerto o matriz de puertos que se deben reenviar localmente de forma automática cuando se ejecuta el entorno.

## <a name="installed-software-specifics"></a>Detalles de software instalado

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition está disponible y en ejecución como servicio local (LocalDB) en el entorno de Windows Codespace. El usuario actual, en el que se ejecuta la aplicación y el terminal de Visual Studio, tiene derechos de administrador de SQL en SQL Server. Para administrar el servidor, tendrá que usar PowerShell en el terminal de Visual Studio u otras herramientas de la línea de comandos, como `dotnet-ef`. Actualmente SQL Server Management Studio y otras herramientas de administración remota no están disponibles.

#### <a name="example-connection-string"></a>Cadena de conexión de ejemplo

A continuación se muestra un ejemplo de una cadena de conexión para conectarse a la instancia local de MS SQL Server.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

La CLI de Azure se instala en todos los entornos de Windows Codespace y está disponible en la ruta de acceso como `az`.

#### <a name="using-azure-resources"></a>Uso de recursos de Azure

Si usa una identidad de Azure Active Directory para autenticar la aplicación en recursos de Azure, tendrá que iniciar sesión primero en Azure desde el terminal de Visual Studio. Para iniciar sesión, use el comando `login` de la CLI de Azure con el flujo de inicio de sesión del dispositivo (tal y como se muestra en el ejemplo siguiente). Cuando haya iniciado sesión, la sesión de terminal y de aplicación deberían poder usar esa identidad.

```powershell
> az login --use-device-code
```

Puede obtener más información sobre el comando `az login` en la [documentación](/cli/azure/reference-index#az_login) de la CLI de Azure.

## <a name="see-also"></a>Consulte también

- [¿Qué es GitHub Codespaces?](codespaces-overview.md)
- [Uso de Visual Studio con un codespace](use-visual-studio-with-codespaces.md)