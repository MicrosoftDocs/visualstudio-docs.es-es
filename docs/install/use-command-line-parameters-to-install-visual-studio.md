---
title: Usar parámetros de la línea de comandos para instalar Visual Studio
titleSuffix: ''
description: Obtenga información sobre cómo usar parámetros de línea de comandos para controlar o personalizar la instalación de Visual Studio.
ms.date: 4/16/2021
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 23c83611e7663d35b229517f1e0224eb4ae7bb57
ms.sourcegitcommit: 367a2d9df789aa617abaa09b0cd0a18db7357d0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107800800"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usar parámetros de la línea de comandos para instalar Visual Studio

Al instalar Visual Studio mediante programación o desde un símbolo del sistema, puede usar diversos parámetros de la línea de comandos para controlar o personalizar la instalación a fin de hacer lo siguiente:

- Iniciar la instalación en el cliente con determinadas opciones y comportamientos preseleccionados.
- Automatizar el proceso de instalación.
- Crear o mantener un diseño de red de los archivos de producto para instalar o actualizar máquinas cliente.

Las opciones de línea de comandos se pueden usar con el programa previo de instalación, que es el archivo pequeño (~1 MB) que inicia el proceso de descarga, o bien con el paquete de actualización de administrador, que se implementa en el [Catálogo de Microsoft Update](https://catalog.update.microsoft.com). 

::: moniker range="vs-2017"

Para obtener la versión más reciente del programa previo para la versión 15.9 de Visual Studio 2017, vaya a la página de [**versiones anteriores de Visual Studio**](https://visualstudio.microsoft.com/vs/older-downloads/) y descargue uno de estos archivos de programa previo:

| Edición | Filename |
|-------------|-----------------------|
|Visual Studio Enterprise 2017 versión 15.9 | vs_enterprise.exe |
|Visual Studio Professional 2017 versión 15.9 | vs_professional.exe |
|Visual Studio Build Tools 2017 versión 15.9  | vs_buildtools.exe |

::: moniker-end

::: moniker range="vs-2019"

Puede obtener el programa previo de Visual Studio 2019 desde la [página de descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) o la página de [versiones de Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history#installing-an-earlier-release) para la versión y edición elegidas de Visual Studio. El archivo de instalación (o programa previo) se corresponderá o será parecido a uno de los siguientes:

| Edición                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Visual Studio 2019 Enterprise   | [vs_enterprise.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Professional | [vs_professional.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019) |
| Visual Studio 2019 Build Tools   | [vs_buildtools.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=buildtools&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)     |
| Visual Studio 2019 Community    | [vs_community.exe](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=16&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2019)  |

::: moniker-end

::: moniker range="vs-2017"

>[!TIP]
>Si previamente descargó un archivo de programa previo y quiere comprobar su versión, aquí se muestra cómo hacerlo. En Windows, abra el Explorador de archivos, haga clic con el botón derecho en el archivo de programa previo, elija **Propiedades**, seleccione la pestaña **Detalles** y, luego, fíjese en el número de **versión del producto**. Para hacer coincidir ese número con una versión de Visual Studio, consulte la página [Números de compilación y fechas de lanzamiento de Visual Studio](visual-studio-build-numbers-and-release-dates.md).

::: moniker-end

::: moniker range="vs-2019"

>[!TIP]
>Si previamente descargó un archivo de programa previo y desea comprobar su versión, aquí se muestra cómo hacerlo. En Windows, abra el Explorador de archivos, haga clic con el botón derecho en el archivo de programa previo, elija **Propiedades**, seleccione la pestaña **Detalles** y, luego, fíjese en el número de **versión del producto**. Para hacer coincidir ese número con una versión de Visual Studio, consulte la página [Versiones de Visual Studio 2019](https://docs.microsoft.com/visualstudio/releases/2019/history).

::: moniker-end

Para obtener la actualización del administrador, vaya al [Catálogo de Microsoft Update](https://catalog.update.microsoft.com), busque la actualización que quiera instalar y presione el botón Descargar. Las actualizaciones de administrador asumen que Visual Studio ya está instalado en el equipo. La aplicación de actualizaciones de administrador no iniciará una instalación completamente nueva.

## <a name="bootstrapper-commands-and-command-line-parameters"></a>Comandos del programa previo y parámetros de línea de comandos

Al invocar el programa previo de Visual Studio mediante programación para instalar el producto o mantener un diseño, el primer parámetro es el comando (el verbo) que describe la operación que se va a realizar. Los parámetros de línea de comandos opcionales siguientes, que tienen como prefijo dos guiones (--), definen aún más cómo se supone que se va a realizar esa operación. Ningún parámetro de línea de comandos de Visual Studio distingue entre mayúsculas y minúsculas. En la página [Ejemplos de parámetros de la línea de comandos](command-line-parameter-examples.md) encontrará ejemplos adicionales.

Ejemplo de sintaxis: `vs_enterprise.exe [command] <optional parameters>...`

| **Comando** | **Descripción** |
| ----------------------- | --------------- |
| (en blanco) | El comando predeterminado instala el producto y se usa para todas las operaciones de mantenimiento de diseño. |
| `modify` | Modifica un producto instalado. |
| `update` | Actualiza un producto instalado. |
| `repair` | Repara un producto instalado. |
| `uninstall` | Desinstala un producto instalado. |
| `export` | exporta la selección de instalación a un archivo de configuración de la instalación. **Nota**: Solo se puede utilizar con vs_installer.exe. |


| **Parámetros** | **Descripción** |
| ----------------------- | --------------- |
| `--installPath <dir>` | Para el comando de instalación predeterminado, este parámetro es **Opcional** y describe dónde se instalará la instancia en la máquina cliente. Para otros comandos, como los de actualización o modificación, este parámetro es **Obligatorio** e indica el directorio de instalación sobre el que debe actuar la instancia. |
| `--add <one or more workload or component IDs>` | **Opcional**: durante un comando de instalación o modificación, este parámetro repetible especifica uno o varios id. de componente o carga de trabajo que se van a agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar componentes adicionales de forma global mediante los parámetros `--includeRecommended` o `--includeOptional`. Para incluir varias cargas de trabajo o componentes, repita el comando `--add` (por ejemplo, `--add Workload1 --add Workload2`). Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Para obtener más información, consulte la página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). |
| `--remove <one or more workload or component IDs>` | **Opcional**: durante un comando de modificación, este parámetro repetible especifica uno o varios id. de componente o carga de trabajo que se van a agregar. Complementa y se comporta de forma similar al parámetro `--add`. |
| `--addProductLang <language-locale>` | **Opcional**: durante un comando de instalación o modificación, este parámetro repetible especifica los paquetes de idioma de la interfaz de usuario que se deben instalar con el producto. Si no está presente, la instalación usa el paquete de idioma correspondiente a la configuración regional de la máquina. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--removeProductLang <language-locale>` | **Opcional**: durante un comando de instalación o modificación, este parámetro repetible determina los paquetes de idioma de la interfaz de usuario que se deben quitar del producto.  Complementa y se comporta de forma similar al parámetro `--addProductLang`. |
| `--in <path>` | **Opcional**: URI o ruta de acceso a un [archivo de respuesta](automated-installation-with-response-file.md) que puede contener valores de configuración. |
| `--all` | **Opcional**: durante un comando de instalación o modificación, este parámetro hace que se instalen todas las cargas de trabajo y componentes del producto. |
| `--allWorkloads` | **Opcional**: durante un comando de instalación o modificación, este parámetro instala todas las cargas de trabajo y todos los componentes, pero no los componentes opcionales o recomendados. |
| `--includeRecommended` | **Opcional**: durante un comando de instalación o modificación, este parámetro incluye los componentes recomendados para las cargas de trabajo instaladas, pero no los componentes opcionales. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: durante un comando de instalación o modificación, este parámetro incluye los componentes opcionales para las cargas de trabajo instaladas, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Opcional**: este parámetro, al usarlo con cualquier comando, impide que se muestre una interfaz de usuario mientras se ejecuta el comando. |
| `--passive, -p` | **Opcional**: este parámetro hace que la interfaz de usuario se muestre de forma no interactiva. Este parámetro es mutuamente excluyente del parámetro `--quiet` (y, de hecho, lo invalida).  |
| `--norestart` | **Opcional**: este parámetro se debe emparejar con los parámetros `--passive` o `--quiet`.  Durante un comando de instalación, actualización o modificación, la adición del parámetro `--norestart` retrasará cualquier reinicio necesario. |
| `--force` | **Opcional**: este parámetro fuerza el cierre de Visual Studio, incluso si hay algún proceso de Visual Studio en uso. |
| `--installWhileDownloading` | **Opcional**: durante un comando de instalación, actualización o modificación, este parámetro permite que Visual Studio descargue e instale el producto en paralelo. Es la experiencia predeterminada. |
| `--downloadThenInstall` | **Opcional**: durante un comando de instalación, actualización o modificación, este parámetro obliga a Visual Studio a descargar todos los archivos antes de instalarlos. Es mutuamente excluyente del parámetro `--installWhileDownloading`. |
| `--nickname <name>` | **Opcional**: durante un comando de instalación, este parámetro define el alias que se va a asignar a un producto instalado. El alias no puede tener más de diez caracteres.  |
| `--productKey` | **Opcional**: durante un comando de instalación, este parámetro define la clave del producto que se va a usar para un producto instalado. Se compone de veinticinco caracteres alfanuméricos en formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Muestra una versión sin conexión de esta página. |
| `--config <path>` | **Opcional**: durante una operación de instalación o modificación, esto determina las cargas de trabajo y componentes que se van a agregar en función de un archivo de configuración de instalación guardado anteriormente. Esta operación es aditiva y no quitará ninguna carga de trabajo o componente si no están presentes en el archivo. Además, no se agregarán los elementos que no se aplican al producto. Durante una operación de exportación, esto determina la ubicación para guardar el archivo de configuración de la instalación. |


> [!IMPORTANT]
> Al especificar varias cargas de trabajo, componentes o lenguajes, debe repetir el modificador de la línea de comandos `--add` o `--remove` para cada elemento.

## <a name="layout-command-and-command-line-parameters"></a>Comandos de diseño y parámetros de línea de comandos
Todas las operaciones de administración de diseño asumen que el comando es la instalación predeterminada (en blanco). Por tanto, todas las operaciones de administración de diseño deben comenzar con el parámetro inicial `--layout` obligatorio.  En la tabla siguiente se describen los demás parámetros que puede usar para crear o actualizar un diseño mediante la línea de comandos.

| **Parámetros de diseño** | **Descripción** |
| ----------------------- | --------------- |
| `--layout <dir>` | Especifica un directorio para crear o actualizar una caché de instalación sin conexión. Para obtener más información, consulte [Crear una instalación sin conexión de Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcional**: se usa con `--layout` para preparar una caché de instalación sin conexión con paquetes de recursos con los idiomas especificados. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante `--includeRecommended` o `--includeOptional`. Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Para obtener más información, consulte la página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). <br/>**Nota**: Si se usa `--add`, solo se descargan las cargas de trabajo y los componentes especificados y sus dependencias. Si no se especifica `--add`, todos los componentes y las cargas de trabajo se descargan en el diseño.|
| `--includeRecommended` | **Opcional**: incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: incluye los componentes recomendados *y* opcionales para las cargas de trabajo que se incluyen en el diseño. Las cargas de trabajo se especifican con `--add`.  |
| `--keepLayoutVersion` | **Opcional**: es posible aplicar cambios en el diseño sin actualizar su versión. |
| `--verify` | **Opcional**: es posible comprobar el contenido del diseño. Se muestra una lista con los archivos dañados o que no se hayan encontrado. |
| `--fix` | **Opcional**: es posible comprobar el contenido del diseño.  Si faltan archivos o están dañados, se vuelven a descargar. Para corregir el diseño, es necesario tener acceso a Internet. |
| `--clean <one or more paths to catalogs>` | **Opcional**: quita las versiones anteriores de los componentes de un diseño que se ha actualizado a una versión más reciente. |

| **Parámetros de diseño avanzados** | **Descripción** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcional**: identificador del canal correspondiente a la instancia que se va a instalar. Es necesario para el comando de instalación, y se omite para otros comandos si se especifica `--installPath`. |
| `--channelUri <uri>` | **Opcional**: el URI del manifiesto del canal. Si no se quieren las actualizaciones, `--channelUri` puede apuntar a un archivo no existente (por ejemplo,--channelUri C:\doesntExist.chman). Esto puede usarse para el comando de instalación; se omite para los demás comandos. |
| `--installChannelUri <uri>` | **Opcional**: el URI del manifiesto del canal que se va a usar para la instalación. El URI especificado por `--channelUri`, que debe especificarse cuando se especifica `--installChannelUri`, se usa para detectar actualizaciones. Esto puede usarse para el comando de instalación; se omite para los demás comandos. |
| `--installCatalogUri <uri>` | **Opcional**: el URI del manifiesto del catálogo que se va a usar para la instalación. Si se especifica, el administrador del canal intenta descargar el manifiesto del catálogo de este URI antes de usar el URI en el manifiesto del canal de instalación. Este parámetro se usa para admitir la instalación sin conexión, donde la caché de diseño se creará con el catálogo del producto que ya se ha descargado. Esto puede usarse para el comando de instalación; se omite para los demás comandos. |
| `--productId <id>` | **Opcional**: id. del producto de la instancia que se instalará. Se rellena previamente en condiciones normales de instalación. |
| `--wait` | **Opcional**: el proceso esperará hasta que la instalación se complete antes de devolver un código de salida. Esto es útil al automatizar las instalaciones donde es necesario esperar a que la instalación finalice para controlar el código de retorno de esa instalación. |
| `--locale <language-locale>` | **Opcional**: cambia el idioma para mostrar de la interfaz de usuario del instalador. La configuración se conservará. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--cache` | **Opcional**: si está presente, los paquetes se conservarán después de instalarse de cara a posteriores reparaciones. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `--nocache` | **Opcional**: si está presente, los paquetes se eliminarán después de instalarlos o repararlos. Solo se descargarán de nuevo si es necesario y se volverán a eliminar después de su uso. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Opcional**: si está presente, impide que el instalador se actualice automáticamente cuando se especifica el modo silencioso. El instalador producirá un error en el comando y devolverá un código de salida distinto de cero si se especifica noUpdateInstaller con el modo silencioso cuando se requiere una actualización del instalador. |
| `--noWeb` | **Opcional**: si está presente, la configuración de Visual Studio utiliza los archivos del directorio de diseño para instalar Visual Studio. Si un usuario intenta instalar componentes que no están en el diseño, se produce un error en la instalación.  Para obtener más información, consulte [Implementación de una instalación de red](create-a-network-installation-of-visual-studio.md). <br/><br/> **Importante**: Este modificador no impide que la instalación de Visual Studio busque actualizaciones. Para más información, consulte [Control de actualizaciones a implementaciones de Visual Studio basadas en red](controlling-updates-to-visual-studio-deployments.md). |
| `--path <name>=<path>` | **Opcional**: se usa para especificar rutas de acceso de instalación personalizada para la instalación. Los nombre de ruta de acceso admitidos son uso compartido, caché e instalar. |
| `--path cache=<path>` | **Opcional**: usa la ubicación que especifique para descargar los archivos de instalación. Esta ubicación solo puede establecerse la primera vez que se instala Visual Studio. Ejemplo: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Opcional**: contiene los archivos compartidos para las instalaciones en paralelo de Visual Studio. Algunas herramientas y SDK se instalan en una ubicación en esta unidad, mientras que otros pueden invalidar esta configuración e instalarse en otra unidad. Ejemplo: `--path shared="C:\VS\shared"` <br/><br/>**Importante**: Solo se puede establecer una vez, la primera que se instale Visual Studio. |
| `--path install=<path>` | **Opcional**: equivale a `–-installPath`. En particular, `--installPath "C:\VS"` y `--path install="C:\VS"` son equivalentes. Solo se puede usar uno de estos comandos a la vez. |

## <a name="administrator-update-command-and-command-line-parameters"></a>Comandos de actualización de administrador y parámetros de línea de comandos
Si descarga una actualización de administrador del [Catálogo de Microsoft Update](https://catalog.update.microsoft.com) en el directorio de instalación de la máquina cliente, puede hacer doble clic en el archivo para aplicar la actualización. También puede abrir una ventana de comandos y pasar algunos de los parámetros siguientes para cambiar el comportamiento predeterminado. 

Si va a implementar la actualización de administrador a través de Microsoft Endpoint Manager (SCCM), puede modificar el paquete para ajustar el comportamiento mediante los parámetros siguientes. También puede controlar los parámetros mediante un archivo de configuración en la máquina cliente. Para obtener más información, vea [Métodos para configurar una actualización de administrador](../install/applying-administrator-updates.md#methods-for-configuring-an-administrator-update).

Tenga en cuenta que todos los parámetros de actualización de administrador se ejecutan en el contexto de "actualización".

| **Parámetros de actualización de administrador** | **Descripción** |
| ----------------------- | --------------- |
| `--installerUpdateArgs [optional parameters]` | Este parámetro funciona como una "matriz de tránsito" de parámetros específicos que son relevantes para escenarios de actualización de administrador. Los parámetros opcionales que están habilitados para este propósito son los siguientes: <br/><br/> `--quiet`: esta es la experiencia predeterminada para las actualizaciones de administrador y se muestra aquí para proporcionar información completa. <br/> `--passive`: este parámetro invalida el parámetro `--quiet`.  Hace que la interfaz de usuario aparezca de forma no interactiva. <br/>`--norestart`: este parámetro se debe usar junto con `--quiet` o `--passive`, y hace que se retrasen los reinicios necesarios. <br/>`--noWeb`: este parámetro impide que Visual Studio compruebe en Internet si hay actualizaciones para el producto. <br/>`--force`: este parámetro fuerza el cierre de Visual Studio, incluso si está en uso. Use este parámetro con precaución, ya que podría provocar la pérdida del trabajo. Este parámetro se debe usar en el contexto del usuario. <br/>`--installWhileDownloading`: este parámetro permite a Visual Studio descargar e instalar el producto en paralelo. Es la experiencia predeterminada para las actualizaciones de administrador y se muestra aquí para proporcionar información completa. <br/>`--downloadThenInstall`: este parámetro obliga a Visual Studio a descargar todos los archivos antes de instalarlos. Es mutuamente excluyente del parámetro `--installWhileDownloading`. |
| `--checkPendingReboot` | La actualización se anulará si hay un reinicio pendiente en la máquina, independientemente de la aplicación que pueda haberlo provocado. El valor predeterminado es no comprobar si hay reinicios pendientes. |


Ejemplo de sintaxis: `visualstudioupdate-16.9.0to16.9.4.exe --installerUpdateArgs=--force,--noWeb --checkPendingReboot`

## <a name="list-of-workload-ids-and-component-ids"></a>Lista de los id. de carga de trabajo y los id. de componente

Para una lista de los identificadores de componente y carga de trabajo ordenados por producto de Visual Studio, consulte la página [Identificadores de componente y carga de trabajo de Visual Studio](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma

| **Idioma-configuración regional** | **Lenguaje** |
| ----------------------- | --------------- |
| Cs-cz | Checo |
| De-de | Alemán |
| En-us | Inglés |
| Es-es | Español |
| Fr-fr | Francés |
| It-it | Italiano |
| Ja-jp | Japonés |
| Ko-kr | Coreano |
| Pl-pl | Polaco |
| Pt-br | Portugués (Brasil) |
| Ru-ru | Ruso |
| Tr-tr | Turco |
| Zh-cn | Chino (simplificado) |
| Zh-tw | Chino (tradicional) |

## <a name="error-codes"></a>Códigos de error

En función del resultado de la operación, la variable de entorno `%ERRORLEVEL%` se establece en uno de los valores siguientes:

[!INCLUDE[install-error-codes-md](includes/install-error-codes-md.md)]

Cada operación genera varios archivos de registro en el directorio `%TEMP%` que indican el progreso de la instalación. Ordene la carpeta por fecha y busque los archivos que empiecen por `dd_bootstrapper`, `dd_client` y `dd_setup` para el programa previo, la aplicación del instalador y el motor de configuración, respectivamente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulta también

- [Ejemplos de parámetros de la línea de comandos para la instalación de Visual Studio](command-line-parameter-examples.md)
- [Crear una instalación sin conexión de Visual Studio](create-an-offline-installation-of-visual-studio.md)
- [Automatizar la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
- [Identificadores de cargas de trabajo y componentes de Visual Studio](workload-and-component-ids.md)
