---
title: "Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 0f07824b29e7851e353d472838a897853e227d6c
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio 2017
Para ilustrar el [uso de los parámetros de línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md), incluimos aquí varios ejemplos que puede personalizar para satisfacer sus necesidades.

En cada uno de los ejemplos, `vs_enterprise.exe`, `vs_professional.exe` y `vs_community.exe` representan la edición correspondiente del programa previo de Visual Studio, que es el archivo pequeño (de aproximadamente 1 MB) que inicia el proceso de descarga. Si usa una edición diferente, reemplácelo por el nombre del programa previo adecuado.

> [!NOTE]
> Todos los comandos requieren de elevación administrativa, y se mostrará un mensaje de Control de cuentas de usuario si el proceso no se inicia desde un símbolo del sistema con privilegios elevados.

> [!NOTE]
>  Puede usar el carácter `^` al final de una línea de comandos para concatenar varias líneas en un solo comando. Como alternativa, puede simplemente colocar estas líneas juntas en una sola fila. En PowerShell, el equivalente es el carácter de comilla simple (`` ` ``). 

* Instale una instancia mínima de Visual Studio, en la que no hay solicitudes interactivas pero se muestra el progreso:
```
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Instale una instancia de escritorio de Visual Studio en modo silencioso, con el paquete de idioma francés, que solo se devuelve cuando el producto está instalado.
```
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --includeRecommended --quiet --wait
```

> [!NOTE]
>  El parámetro `--wait` está diseñado para su uso en un archivo por lotes. En un archivo por lotes, la ejecución del comando siguiente no continuará hasta que se haya completado la instalación. La variable de entorno `%ERRORLEVEL%` contendrá el valor devuelto del comando, como se indica en la página [Usar parámetros de la línea de comandos para instalar Visual Studio ](use-command-line-parameters-to-install-visual-studio.md).

* Descargue el editor principal de Visual Studio (la configuración mínima de Visual Studio). Incluya solo el paquete de idioma inglés:

```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor
```

* Descargue las cargas de trabajo de escritorio de .NET y web de .NET junto con todos los componentes recomendados y la extensión de GitHub. Incluya solo el paquete de idioma inglés:
```
vs_community.exe --layout C:\VS2017 ^
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Component.GitHub.VisualStudio ^
   --includeRecommended
```

* Inicie una instalación interactiva de todas las cargas de trabajo y los componentes que están disponibles en Visual Studio 2017 Enterprise Edition:
```
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Instale una segunda instancia con nombre de Visual Studio 2017 Professional en un equipo con Visual Studio 2017 Community Edition ya instalado, con compatibilidad con el desarrollo de Node.js:
```
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --includeRecommended --nickname VSforNode
```

* Quite de la instancia predeterminada de Visual Studio instalada el componente Herramientas de generación de perfiles:
```
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

## <a name="see-also"></a>Vea también

 * [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

