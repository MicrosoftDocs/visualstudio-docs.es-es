---
title: Ejemplos de parámetros de la línea de comandos para la instalación
description: Personalice estos ejemplos para crear su propia instalación de la línea de comandos de Visual Studio.
ms.date: 01/16/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87b8c1d71b3ed1ee03433fd2720a86cf0ee3e6a2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "57872104"
---
# <a name="command-line-parameter-examples-for-visual-studio-installation"></a>Ejemplos de parámetros de la línea de comandos para la instalación de Visual Studio

Para ilustrar el [uso de los parámetros de línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md), incluimos aquí varios ejemplos que puede personalizar para satisfacer sus necesidades.

En cada uno de los ejemplos, `vs_enterprise.exe`, `vs_professional.exe` y `vs_community.exe` representan la edición correspondiente del programa previo de Visual Studio, que es el archivo pequeño (de aproximadamente 1 MB) que inicia el proceso de descarga. Si usa una edición diferente, reemplácelo por el nombre del programa previo adecuado.

> [!NOTE]
> Todos los comandos requieren de elevación administrativa, y se mostrará un mensaje de Control de cuentas de usuario si el proceso no se inicia desde un símbolo del sistema con privilegios elevados.
>
> [!NOTE]
> Puede usar el carácter `^` al final de una línea de comandos para concatenar varias líneas en un solo comando. Como alternativa, puede simplemente colocar estas líneas juntas en una sola fila. En PowerShell, el equivalente es el carácter de comilla simple (`` ` ``).

Para obtener listas de las cargas de trabajo y los componentes que puede instalar a través de la línea de comandos, consulte la página [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md).

## <a name="using---installpath"></a>Uso de installPath

* Instale una instancia mínima de Visual Studio, en la que no hay solicitudes interactivas pero se muestra el progreso:

  ```cmd
  vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
  ```

* Actualice una instancia de Visual Studio mediante la línea de comandos, en la que no hay solicitudes interactivas pero se muestra el progreso:

  ```cmd
  vs_enterprise.exe --update --quiet --wait
  vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
  ```

  > [!NOTE]
  > Ambos comandos son necesarios. El primer comando actualiza el instalador de Visual Studio. El primer comando actualiza la instancia de Visual Studio. Para evitar que aparezca un cuadro de diálogo de Control de cuentas de usuario, ejecute el símbolo del sistema como administrador.

* Instale una instancia de escritorio de Visual Studio en modo silencioso, con el paquete de idioma francés, que solo se devuelve cuando el producto está instalado.

  ```cmd
  vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
  ```

## <a name="using---wait"></a>Uso de --wait

* Se usa en scripts o archivos por lotes para esperar que el instalador de Visual Studio se complete antes de ejecutar el comando siguiente. En el caso de los archivos por lotes, una variable de entorno `%ERRORLEVEL%` contendrá el valor devuelto del comando, como se indica en la página [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md). Algunas utilidades de comandos requieren parámetros adicionales para esperar la finalización y para obtener el valor devuelto del instalador. El siguiente es un ejemplo de los parámetros adicionales que se usan con el comando de script "Start-Process" de PowerShell:

  ```cmd
  $exitCode = Start-Process -FilePath vs_enterprise.exe -ArgumentList "install", "--quiet", "--wait" -Wait -PassThru
  ```
  
* El primer "--wait" lo usa el Instalador de Visual Studio y el segundo "-Wait" lo usa "Start-Process" para esperar la finalización. El parámetro "-PassThru" lo usa "Start-Process" para usar el código de salida del instalador por su valor devuelto.
  
## <a name="using---layout"></a>Uso de layout

* Descargue el editor principal de Visual Studio (la configuración mínima de Visual Studio). Incluya solo el paquete de idioma inglés:

  ```cmd
  vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
  ```

* Descargue las cargas de trabajo de escritorio de .NET y web de .NET junto con todos los componentes recomendados y la extensión de GitHub. Incluya solo el paquete de idioma inglés:

  ```cmd
  vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
  ```

## <a name="using---all"></a>Uso de --all

* Inicie una instalación interactiva de todas las cargas de trabajo y los componentes que están disponibles en Visual Studio 2017 Enterprise Edition:

  ```cmd
  vs_enterprise.exe --all
  ```

## <a name="using---includerecommended"></a>Uso de includeRecommended

* Instale una segunda instancia con nombre de Visual Studio 2017 Professional en un equipo con Visual Studio 2017 Community Edition ya instalado, con compatibilidad con el desarrollo de Node.js:

  ```cmd
  vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
  ```

## <a name="using---remove"></a>Uso de remove

* Quite de la instancia predeterminada de Visual Studio instalada el componente Herramientas de generación de perfiles:

  ```cmd
  vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
  ```

## <a name="using---path"></a>Uso de path

Estos parámetros de línea de comandos son **nuevos en 15.7**. Para obtener más información sobre ellos, vea la página [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md).

* Uso de las rutas de acceso instalar, caché y uso compartido:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache" --path shared="C:\VS\shared"`

* Uso de solo las rutas de acceso instalar y caché:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path cache="C:\VS\cache"`

* Uso de solo las rutas de acceso instalar y uso compartido:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS" --path shared="C:\VS\shared"`

* Uso de solo la ruta de acceso instalar:

  `vs_enterprise.exe --add Microsoft.VisualStudio.Workload.CoreEditor --path install="C:\VS"`

## <a name="using-export"></a>Uso de exportación

Este comando de línea de comandos es **nuevo en 15.9**. Para obtener más información sobre él, vea la página [Uso de parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

* Uso de la exportación para guardar la selección de la instalación:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --installPath "C:\VS" --config "C:\.vsconfig"
```

* Uso de la exportación para guardar la selección personalizada desde cero:

```cmd
"C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe" export --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --config "C:\.vsconfig"
```

## <a name="using---config"></a>Uso de --config

Este parámetro de línea de comandos es **nuevo en 15.9**. Para obtener más información sobre él, vea la página [Uso de parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md).

* Uso de --config para instalar los componentes y cargas de trabajo desde un archivo de configuración de instalación guardado anteriormente:

```cmd
vs_enterprise.exe --config "C:\.vsconfig" --installPath "C:\VS"
```

* Uso de --config para agregar componentes y cargas de trabajo a una instalación existente:

```cmd
vs_enterprise.exe modify --installPath "C:\VS" --config "C:\.vsconfig"
```


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
