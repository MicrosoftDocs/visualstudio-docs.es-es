---
title: "Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
author: timsneath
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f91810f53a27cc988c44e6c283364bb2d29e39e0
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
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

* Actualice una instancia de Visual Studio mediante la línea de comandos, en la que no hay solicitudes interactivas pero se muestra el progreso:
```
vs_enterprise.exe --update --quiet --wait
vs_enterprise.exe update --wait --passive --norestart --installPath "C:\installPathVS"
```

> [!NOTE]
> Ambos comandos son necesarios. El primer comando actualiza el instalador de Visual Studio. El primer comando actualiza la instancia de Visual Studio. Para evitar que aparezca un cuadro de diálogo de Control de cuentas de usuario, ejecute el símbolo del sistema como administrador. 

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

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

 * [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
 * [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
