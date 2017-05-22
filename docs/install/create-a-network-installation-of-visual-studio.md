---
title: "Creación de una instalación basada en red de Visual Studio | Microsoft Docs"
description: "{{MARCADOR DE POSICIÓN}}"
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
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
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: es-es
ms.lasthandoff: 05/09/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>Creación de una instalación de red de Visual Studio 2017

Normalmente, un administrador de empresa creará un punto de instalación de red para la implementación en estaciones de trabajo cliente. Visual Studio 2017 se ha diseñado para permitirle almacenar en caché los archivos de la instalación inicial, junto con todas las actualizaciones del producto, en una única carpeta (lo que se conoce en ocasiones como _creación de un diseño_), de modo que las estaciones de trabajo clientes puedan usar la misma ubicación de red para administrar sus instalaciones, incluso si no se ha actualizado aún la última actualización de servicio.

> [!NOTE]
> Si tiene varias ediciones de Visual Studio en uso dentro de su empresa (por ejemplo, Visual Studio Professional y Visual Studio Enterprise), deberá crear un recurso compartido de instalación de red aparte para cada edición.

## <a name="download-the-visual-studio-bootstrapper"></a>Descarga del programa previo de Visual Studio
**Descargue** la edición de Visual Studio que desee. Asegúrese de hacer clic en **Guardar** y, a continuación, haga clic en **Abrir carpeta**.

El archivo ejecutable&mdash;o, para ser más específico, un archivo de programa previo&mdash;coincidirá con uno de los siguientes.

|Edición | Descargar|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Comunidad de Visual Studio | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

Otros programas previos admitidos incluyen [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) y [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Creación de una carpeta de instalación sin conexión
Para crear una instalación sin conexión con todos los lenguajes y todas las características, utilice uno de los comandos de los ejemplos siguientes.

(Asegúrese de ejecutar el comando desde el directorio de descarga. Normalmente, es `C:\Users\<username>\Downloads` en un equipo que ejecuta Windows 10).

- Para Visual Studio Enterprise, ejecute:
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- Para Visual Studio Professional, ejecute:
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- Para Visual Studio Community, ejecute:
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>Modificación del archivo response.json
Puede modificar el archivo response.json para establecer valores predeterminados que se usarán cuando se ejecute el programa de instalación.  Por ejemplo, puede configurar el archivo `response.json` para elegir un conjunto específico de cargas de trabajo que se seleccionan automáticamente.
Consulte [Automatización de la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md) para más información.

## <a name="copy-the-layout-to-a-network-share"></a>Copia del diseño en un recurso compartido de red

Hospede el diseño en un recurso compartido de red para que se pueda ejecutar desde otras máquinas.
* Ejemplo:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>Personalización del diseño de red
Existen varias opciones que puede usar para personalizar el diseño de red. Puede crear un diseño parcial que solo contenga un conjunto específico de [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [cargas de trabajo y componentes, y sus dependencias recomendados u opcionales](workload-and-component-ids.md). Esta opción puede resultar útil si sabe que solo va a implementar un subconjunto de las cargas de trabajo en las estaciones de trabajo cliente. Entre los parámetros de línea de comandos comunes para personalizar el diseño se incluyen:

 - ```--add``` para especificar [identificadores de carga de trabajo o componente](workload-and-component-ids.md).  Si se usa `--add`, solo se descargan esas cargas de trabajo y componentes especificados con `--add`.  Si no se usa `--add`, se descargarán todos los componentes y cargas de trabajo.
 - ```--includeRecommended``` para incluir todos los componentes recomendados para los identificadores de carga especificados.
 - ```--includeOptional``` para incluir todos los componentes recomendados y opcionales para los identificadores de carga de trabajo especificados.
 - ```--lang``` para especificar [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).
 
Estos son algunos ejemplos de cómo crear un diseño parcial personalizado.

 - Para descargar todas las cargas de trabajo y los componentes para un solo idioma, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Para descargar todas las cargas de trabajo y los componentes para varios idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Para descargar una carga de trabajo para todos los idiomas, ejecute: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - Para descargar dos cargas de trabajo y un componente opcional para tres idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - Para descargar dos cargas de trabajo y todos sus componentes recomendados, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - Para descargar dos cargas de trabajo y todos sus componentes recomendados y opcionales, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>Implementación de una instalación de red
Los administradores pueden implementar Visual Studio en estaciones de trabajo cliente como parte de un script de instalación. O bien, los usuarios que tienen derechos de administrador pueden ejecutar la instalación directamente desde el recurso compartido para instalar Visual Studio en sus máquinas.

- Los usuarios pueden realizar la instalación mediante la ejecución de: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Los administradores pueden realizar la instalación en modo desatendido mediante la ejecución de: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Cuando se ejecuta como parte de un archivo por lotes, la opción `--wait` garantiza que el proceso `vs_enterprise.exe` espera hasta que la instalación ha finalizado antes de devolver un código de salida. Esta opción resulta de utilidad en aquellos casos en los que un administrador de empresa desea realizar acciones adicionales sobre la instalación finalizada (por ejemplo, para [aplicar una clave de producto a una instalación correcta](automatically-apply-product-keys-when-deploying-visual-studio.md)). Esto es útil al automatizar las instalaciones donde es necesario esperar a que la instalación finalice para controlar el código de retorno de esa instalación.  Si no usa `--wait`, el proceso vs_enterprise.exe finalizará antes de que se complete la instalación y no devolverá un código de salida exacto que representa el estado de la operación de instalación.

### <a name="error-codes"></a>Códigos de error
Si usó el parámetro `--wait`, la variable de entorno `%ERRORLEVEL%` se establecerá en uno de los siguientes valores, según el resultado de la operación:

  | **Valor** | **Resultado** |
  | --------- | ---------- |
  | 0 | Operación completada correctamente |
  | 3010 | Operación completada correctamente, pero la instalación requiere reiniciar el equipo para que se pueda usar |
  | Otros | Condición de error: consulte los registros para obtener más información |

## <a name="updating-a-network-install-layout"></a>Actualización de un diseño de instalación de red
A medida que estén disponibles actualizaciones de productos, puede que quiera [actualizar el diseño de instalación de red](update-a-network-installation-of-visual-studio.md) para incorporar paquetes actualizados.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Creación de un diseño para una versión anterior de Visual Studio 2017
**Nota**: Los programas previos de VS 2017 disponibles en http://www.visualstudio.com descargarán e instalarán la versión de VS 2017 más reciente disponible cada vez que se ejecuten. Si descarga hoy mismo un programa previo de VS y lo ejecuta durante 6 meses a partir de ahora, se instalará la versión de VS 2017 que estaba disponible en ese momento posterior. Si crea un diseño, al instalar VS desde ese diseño se instalará la versión específica de VS que existe en el diseño. Aunque es posible que exista una versión más reciente en línea, obtendrá la versión de VS que está en el diseño.

Si necesita crear un diseño para una versión anterior de Visual Studio 2017, puede ir a https://my.visualstudio.com para descargar versiones "fijas" de los programas previos de Visual Studio 2017 de las versiones admitidas. Esto le permitirá crear un diseño de instalación de red para esa versión anterior. 

### <a name="how-to-get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión
Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es utilizar la herramienta [Notificar un problema	](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

Tenemos también otras opciones de soporte técnico disponibles. Para ver un listado, consulte la página [Hable con nosotros](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)

