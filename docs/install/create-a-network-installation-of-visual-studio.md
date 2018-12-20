---
title: Creación de una instalación basada en red
description: Obtenga información sobre cómo crear un punto de instalación de red para la implementación de Visual Studio dentro de una empresa.
ms.date: 10/17/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb259e1b6b90b93d01cdabd5622e0397d037c250
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159456"
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Creación de una instalación de red de Visual Studio 2017

Normalmente, un administrador de empresa crea un punto de instalación de red para la implementación en estaciones de trabajo cliente. Hemos diseñado Visual Studio 2017 para permitirle almacenar en caché los archivos de la instalación inicial junto con todas las actualizaciones de producto en una única carpeta. Este proceso también se conoce como la _creación de un diseño_. Hemos realizado esto para que las estaciones de trabajo de cliente puedan usar la misma ubicación de red para administrar su instalación incluso si todavía no han actualizado a la última actualización del servicio.

 > [!NOTE]
 > Si tiene varias ediciones de Visual Studio en uso dentro de su empresa (por ejemplo, Visual Studio Professional y Visual Studio Enterprise), debe crear un recurso compartido de instalación de red aparte para cada edición.

## <a name="download-the-visual-studio-bootstrapper"></a>Descarga del programa previo de Visual Studio

**Descargue** la edición de Visual Studio que desee. Asegúrese de hacer clic en **Guardar** y, a continuación, haga clic en **Abrir carpeta**.

El archivo ejecutable o, para ser más específicos, un archivo de programa previo, debe coincidir con uno de los siguientes.

|Edición | Descargar|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Comunidad de Visual Studio | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Otros programas previos admitidos incluyen [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) y [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Creación de una carpeta de instalación sin conexión

Deberá disponer de conexión a Internet para poder completar este paso. Para crear una instalación sin conexión con todos los lenguajes y todas las características, utilice uno de los comandos de los ejemplos siguientes.

   > [!IMPORTANT]
   > Un diseño de Visual Studio 2017 completo requiere al menos 35 GB de espacio en disco y puede tardar algún tiempo en descargarse.  Consulte la sección [Customizing the network layout](#customizing-the-network-layout) (Personalización del diseño de red) para detalles sobre cómo crear un diseño únicamente con los componentes que desea instalar.
   >
   > [!TIP]
   > Asegúrese de ejecutar el comando desde el directorio de descarga. Normalmente, es `C:\Users\<username>\Downloads` en un equipo que ejecuta Windows 10.

- Para Visual Studio Enterprise, ejecute:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Para Visual Studio Professional, ejecute:

  ```vs_professional.exe --layout c:\vs2017offline```

- Para Visual Studio Community, ejecute:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Modificación del archivo response.json

Puede modificar el archivo response.json para establecer valores predeterminados que se usan cuando se ejecuta el programa de instalación.  Por ejemplo, puede configurar el archivo `response.json` para elegir un conjunto específico de cargas de trabajo que se seleccionan automáticamente.
Consulte [Automatización de la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md) para más información.

## <a name="copy-the-layout-to-a-network-share"></a>Copia del diseño en un recurso compartido de red

Hospede el diseño en un recurso compartido de red para que se pueda ejecutar desde otras máquinas.
* Ejemplo:<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```

## <a name="customizing-the-network-layout"></a>Personalización del diseño de red

Existen varias opciones que puede usar para personalizar el diseño de red. Puede crear un diseño parcial que solo contenga un conjunto específico de [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [cargas de trabajo y componentes, y sus dependencias recomendados u opcionales](workload-and-component-ids.md). Esta opción puede resultar útil si sabe que solo va a implementar un subconjunto de las cargas de trabajo en las estaciones de trabajo cliente. Entre los parámetros de línea de comandos comunes para personalizar el diseño se incluyen:

* ```--add``` para especificar [identificadores de carga de trabajo o componente](workload-and-component-ids.md).  Si se usa `--add`, solo se descargan esas cargas de trabajo y componentes especificados con `--add`.  Si no se usa `--add`, se descargan todos los componentes y cargas de trabajo.
* ```--includeRecommended``` para incluir todos los componentes recomendados para los identificadores de carga especificados.
* ```--includeOptional``` para incluir todos los componentes recomendados y opcionales para los identificadores de carga de trabajo especificados.
* ```--lang``` para especificar [configuraciones regionales de idioma](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Estos son algunos ejemplos de cómo crear un diseño parcial personalizado.

* Para descargar todas las cargas de trabajo y los componentes para un solo idioma, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
* Para descargar todas las cargas de trabajo y los componentes para varios idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
* Para descargar una carga de trabajo para todos los idiomas, ejecute: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
* Para descargar dos cargas de trabajo y un componente opcional para tres idiomas, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
* Para descargar dos cargas de trabajo y todos sus componentes recomendados, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
* Para descargar dos cargas de trabajo y todos sus componentes recomendados y opcionales, ejecute: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```

### <a name="new-in-153"></a>Novedades de la versión 15.3

Cuando ejecuta un comando de diseño, las opciones que especifique se guardan, como las cargas de trabajo y los idiomas. Los comandos de diseño posteriores incluirán todas las opciones anteriores.  Aquí se muestra un ejemplo de un diseño con una carga de trabajo solo para inglés:

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US```

Si quiere actualizar ese diseño a una versión más reciente, no tiene que especificar ningún parámetro de línea de comandos adicional. Las opciones anteriores se guardan y se usan mediante cualquier comando de diseño posterior en esta carpeta de diseño.  El comando siguiente actualizará el diseño parcial existente.

```vs_enterprise.exe --layout c:\VS2017Layout```

Si quiere agregar una carga de trabajo adicional, aquí se muestra un ejemplo de cómo realizarlo. En este caso, agregaremos la carga de trabajo de Azure y un idioma localizado.  Ahora tanto el escritorio administrado como Azure se incluyen en este diseño.  Los recursos de idioma para inglés y alemán se incluyen para todas estas cargas de trabajo. El diseño se actualiza a la última versión disponible.

```vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE```

Si quiere actualizar un diseño existente en un diseño completo, use la opción --all, como se muestra en el ejemplo siguiente.

```vs_enterprise.exe --layout c:\VS2017Layout --all```

## <a name="deploying-from-a-network-installation"></a>Implementación de una instalación de red

Los administradores pueden implementar Visual Studio en estaciones de trabajo cliente como parte de un script de instalación. O bien, los usuarios que tienen derechos de administrador pueden ejecutar la instalación directamente desde el recurso compartido para instalar Visual Studio en sus máquinas.

- Los usuarios pueden realizar la instalación mediante la ejecución de: <br>```\\server\products\VS2017\vs_enterprise.exe```
- Los administradores pueden realizar la instalación en modo desatendido mediante la ejecución de: <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> Cuando se ejecuta como parte de un archivo por lotes, la opción `--wait` garantiza que el proceso `vs_enterprise.exe` espere hasta que la instalación haya finalizado antes de devolver un código de salida. Resulta muy útil si un administrador de empresa quiere realizar más acciones en una instalación completada (por ejemplo, para [aplicar una clave de producto a una instalación correcta](automatically-apply-product-keys-when-deploying-visual-studio.md)), pero debe esperar a que la instalación finalice para controlar el código de retorno desde esa instalación.  Si no usa `--wait`, el proceso `vs_enterprise.exe` se cierra antes de que la instalación se complete y devuelve un código de salida incorrecto que no representa el estado de la operación de instalación.

Cuando realice la instalación desde un diseño, el contenido que está instalado se adquirirá del diseño. Pero si selecciona un componente que no está en el diseño, se obtendrá de Internet.  Si quiere evitar que la instalación de Visual Studio descargue cualquier contenido que no esté en su diseño, use la opción `--noWeb`.  Si se usa `--noWeb` y al diseño le falta cualquier contenido seleccionado que se va a instalar, se produce un error en la instalación.

### <a name="error-codes"></a>Códigos de error

Si ha usado el parámetro `--wait`, la variable de entorno `%ERRORLEVEL%` se establece en uno de los siguientes valores, según el resultado de la operación:

  | **Valor** | **Resultado** |
  | --------- | ---------- |
  | 0 | Operación completada correctamente |
  | 3010 | Operación completada correctamente, pero la instalación requiere reiniciar el equipo para que se pueda usar |
  | Otros | Condición de error: consulte los registros para obtener más información |

## <a name="updating-a-network-install-layout"></a>Actualización de un diseño de instalación de red

A medida que estén disponibles actualizaciones de productos, puede que quiera [actualizar el diseño de instalación de red](update-a-network-installation-of-visual-studio.md) para incorporar paquetes actualizados.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Creación de un diseño para una versión anterior de Visual Studio 2017

> [!NOTE]
> Los programas previos de Visual Studio 2017 que están disponibles en [visualstudio.microsoft.com](http://visualstudio.microsoft.com) descargan e instalan la versión de Visual Studio 2017 más reciente disponible cada vez que se ejecutan. Si descarga hoy mismo un programa previo de Visual Studio y lo ejecuta durante seis meses a partir de ahora, se instala la versión de Visual Studio 2017 que está disponible en ese momento posterior. Si crea un diseño, al instalar Visual Studio desde ese diseño se instala la versión específica de Visual Studio que existe en el diseño. Aunque es posible que exista una versión más reciente en línea, obtiene la versión de Visual Studio que está en el diseño.

Si necesita crear un diseño para una versión anterior de Visual Studio 2017, puede ir a https://my.visualstudio.com para descargar versiones "no editables" de los programas previos de Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Obtención de soporte técnico para el instalador sin conexión

Si experimenta un problema con la instalación sin conexión, queremos saberlo. La mejor manera para hacérnoslo saber es usar la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con esta herramienta puede enviarnos la telemetría y los registros que necesitamos para ayudarnos a diagnosticar y corregir el problema.

También dispone de la opción del [**chat en directo**](https://visualstudio.microsoft.com/vs/support/#talktous) de soporte técnico para problemas relacionados con la instalación (disponible solo en inglés).

Tenemos también otras opciones de soporte técnico disponibles. Para obtener un listado, vea nuestra página [Hable con nosotros](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
