---
title: "Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: 4e33dc3ebb32569b547aa9bcb6db9a15dbe4fc21
ms.openlocfilehash: ff67313f350264b39151bc0e2f7191ab16300f24
ms.lasthandoff: 04/05/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio 2017
Para ilustrar el [uso de los parámetros de línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md), incluimos aquí varios ejemplos que puede personalizar para satisfacer sus necesidades.

En cada uno de los ejemplos, `vs_enterprise.exe`, `vs_professional.exe` y `vs_community.exe` representan la edición correspondiente del programa previo de Visual Studio, que es el archivo pequeño (de aproximadamente 1 MB) que inicia el proceso de descarga. Si usa una edición diferente, reemplácelo por el nombre del programa previo adecuado.

> [!NOTE]
> Todos los comandos requieren de elevación administrativa, y se mostrará un mensaje de Control de cuentas de usuario si el proceso no se inicia desde un símbolo del sistema con privilegios elevados.

* Instale una instancia mínima de Visual Studio, en la que no hay solicitudes interactivas pero se muestra el progreso:
```cmd
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* Instale una instancia de escritorio de Visual Studio en modo silencioso, con el paquete de idioma francés, que solo se devuelve cuando el producto está instalado.
```cmd
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --quiet --wait
```

  > [!NOTE]
  >  El parámetro `--wait` está diseñado para su uso en un archivo por lotes. En un archivo por lotes, la ejecución del comando siguiente no continuará hasta que se haya completado la instalación. La variable de entorno `%ERRORLEVEL%` contendrá el valor devuelto del comando, como se indica en la página [Usar parámetros de la línea de comandos para instalar Visual Studio ](use-command-line-parameters-to-install-visual-studio.md).

* Descargue las cargas de trabajo de escritorio de .NET y web de .NET junto con todos los componentes recomendados y la extensión de GitHub. Incluya solo el paquete de idioma inglés:
```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Microsoft.Net.ComponentGroup.TargetingPacks.Common ^
   --add Microsoft.ComponentGroup.Blend ^
   --add Microsoft.VisualStudio.Component.EntityFramework ^
   --add Microsoft.VisualStudio.Component.DiagnosticTools ^
   --add Microsoft.VisualStudio.Component.DockerTools ^
   --add Microsoft.VisualStudio.Component.CloudExplorer ^
   --add Microsoft.VisualStudio.Component.Wcf.Tooling ^
   --add Component.GitHub.VisualStudio
```

   >[!NOTE]
   La edición Enterprise contiene más componentes recomendados que los incluidos aquí. Vea [Directorio de componentes de Visual Studio Enterprise 2017](workload-component-id-vs-enterprise.md) para obtener una lista de todos los componentes recomendados disponibles en Visual Studio Enterprise.

* Inicie una instalación interactiva de todas las cargas de trabajo y los componentes que están disponibles en Visual Studio 2017 Enterprise Edition:
```cmd
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* Instale una segunda instancia con nombre de Visual Studio 2017 Professional en un equipo con Visual Studio 2017 Community Edition ya instalado, con compatibilidad con el desarrollo de Node.js:
```cmd
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --nickname VSforNode
```

* Quite de la instancia predeterminada de Visual Studio instalada el componente Herramientas de generación de perfiles:
```cmd
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

  > [!NOTE]
  >  Puede usar el carácter `^` al final de una línea de comandos para concatenar varias líneas en un solo comando. Como alternativa, puede simplemente colocar estas líneas juntas en una sola fila.

## <a name="see-also"></a>Vea también

 * [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)

