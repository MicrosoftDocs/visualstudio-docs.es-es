---
title: Usar parámetros de la línea de comandos para instalar Visual Studio
description: Obtenga información sobre cómo usar parámetros de línea de comandos para controlar o personalizar la instalación de Visual Studio.
ms.custom: ''
ms.date: 11/14/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e52d61c1226e131c9d989a70f7c8e6432d8f3733
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768512"
---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Uso de parámetros de la línea de comandos para instalar Visual Studio 2017

Cuando instala Visual Studio 2017 desde un símbolo del sistema, puede usar diversos parámetros de la línea de comandos para controlar o personalizar la instalación. Desde la línea de comandos, puede hacer lo siguiente:

- Iniciar la instalación con determinadas opciones preseleccionadas.
- Automatizar el proceso de instalación.
- Crear una caché (diseño) de los archivos de instalación para su uso posterior.

Las opciones de la línea de comandos se usan junto con el programa previo de instalación, que es el archivo pequeño (de aproximadamente 1 MB) que inicia el proceso de descarga. El programa previo es el primer ejecutable que se inicia cuando se realiza la descarga desde el sitio de Visual Studio. Use los vínculos siguientes para obtener un vínculo directo a la versión más reciente del programa previo para la edición del producto que está instalando:

- [Visual Studio 2017 Enterprise](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Professional](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)
- [Visual Studio 2017 Community](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=link+cta&utm_content=download+commandline+parameters+vs2017)

## <a name="list-of-command-line-parameters"></a>Lista de parámetros de la línea de comandos

 Los parámetros de la línea de comandos de Visual Studio no distinguen mayúsculas de minúsculas.

> Sintaxis: `vs_enterprise.exe [command] <options>...`

(Reemplace `vs_enterprise.exe` según corresponda para la edición del producto que está instalando.

>[!TIP]
> Para obtener más ejemplos de cómo usar la línea de comandos para instalar Visual Studio 2017, consulte la página [Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio 2017](command-line-parameter-examples.md)).

| **Comando** | **Descripción** |
| ----------------------- | --------------- |
| (en blanco) | Instala el producto. |
| `modify` | Modifica un producto instalado. |
| `update` | Actualiza un producto instalado. |
| `repair` | Repara un producto instalado. |
| `uninstall` | Desinstala un producto instalado. |
| `export` | **Novedades de 15.9**: exporta la selección de instalación en un archivo de configuración de la instalación. |

| **Opción de instalación** | **Descripción** |
| ----------------------- | --------------- |
| `--installPath <dir>` | El directorio de instalación en el que actuará la instancia. Para el comando de instalación, es **opcional** y es el lugar donde se instalará la instancia. Para otros comandos, es **obligatorio** y es la ubicación en la que se instaló la instancia anteriormente. |
| `--addProductLang <language-locale>` | **Opcional**: durante una operación de instalación o modificación, determina los paquetes de idioma de la interfaz de usuario que se van a instalar con el producto. Puede aparecer varias veces en la línea de comandos para agregar varios paquetes de idioma. Si no está presente, la instalación usa la configuración regional del equipo. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--removeProductLang <language-locale>` | **Opcional**: durante una operación de instalación o modificación, determina los paquetes de idioma de la interfaz de usuario que se van a quitar del producto. Puede aparecer varias veces en la línea de comandos para agregar varios paquetes de idioma. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante `--includeRecommended` o `--includeOptional`. Para incluir varias cargas de trabajo o componentes, repita el comando `--add` (por ejemplo, `--add Workload1 --add Workload2`). Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Para obtener más información, consulte la página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). Puede repetir esta opción según sea necesario.|
| `--remove <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para quitar. Para obtener más información, consulte nuestra página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). Puede repetir esta opción según sea necesario.|
| `--in <path>` | **Opcional**: el URI o la ruta de acceso de un archivo de respuesta.  |
| `--all` | **Opcional**: si se instalan o no todas las cargas de trabajo y componentes para un producto. |
| `--allWorkloads` | **Opcional**: instala todas las cargas de trabajo y los componentes, pero no se instalan los componentes recomendados ni opcionales. |
| `--includeRecommended` | **Opcional**: incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: incluye los componentes opcionales para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Opcional**: no muestra ninguna interfaz de usuario al realizar la instalación. |
| `--passive, -p` | **Opcional**: muestra la interfaz de usuario, pero no solicita ninguna interacción del usuario. |
| `--norestart` | **Opcional**: si está presente, los comandos con `--passive` o `--quiet` no reiniciarán automáticamente la máquina (si es necesario).  Se omite si no se especifica `--passive` ni `--quiet`.  |
| `--nickname <name>` | **Opcional**: esto define el alias que se va a asignar a un producto instalado. El alias no puede tener más de 10 caracteres.  |
| `--productKey` | **Opcional**: esto define la clave del producto que se va a usar para un producto instalado. Se compone de 25 caracteres alfanuméricos en formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Muestra una versión sin conexión de esta página. |
| `--config <path>` | **Opcional** y **nuevo en 15.9**: durante una operación de instalación o modificación, esto determina las cargas de trabajo y componentes que se agregarán en función de un archivo de configuración de instalación guardado anteriormente. Esta operación es aditiva y no quitará ninguna carga de trabajo o componente si no están presentes en el archivo. Además, no se agregarán los elementos que no se aplican al producto. Durante una operación de exportación, esto determina la ubicación para guardar el archivo de configuración de la instalación. |

> Nota: Al especificar varias cargas de trabajo y componentes, debe repetir el modificador de la línea de comandos `--add` o `--remove` para cada elemento.

| **Opciones de diseño** | **Descripción** |
| ----------------------- | --------------- |
| `--layout <dir>` | Especifica un directorio para crear una caché de instalación sin conexión. Para obtener más información, consulte [Crear una instalación sin conexión de Visual Studio 2017](create-a-network-installation-of-visual-studio.md).|
| `--lang <one or more language-locales>` | **Opcional**: se usa con `--layout` para preparar una caché de instalación sin conexión con paquetes de recursos con los idiomas especificados. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante `--includeRecommended` o `--includeOptional`. Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Para obtener más información, consulte la página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). <br/>**Nota**: Si se usa `--add`, solo se descargan las cargas de trabajo y los componentes especificados y sus dependencias. Si no se especifica `--add`, todos los componentes y las cargas de trabajo se descargan en el diseño.|
| `--includeRecommended` | **Opcional**: incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: incluye los componentes recomendados *y* opcionales para las cargas de trabajo que se incluyen en el diseño. Las cargas de trabajo se especifican con `--add`.  |
| `--keepLayoutVersion` | **Novedad de la versión 15.3, opcional**: es posible aplicar cambios en el diseño sin actualizar la versión de este. |
| `--verify` | **Novedad de la versión 15.3, opcional**: es posible comprobar el contenido del diseño. Se muestra una lista con los archivos dañados o que no se hayan encontrado. |
| `--fix` | **Novedad de la versión 15.3, opcional**: es posible comprobar el contenido del diseño.  Si se detecta que faltan archivos o que estos están dañados, se vuelven a descargar. Para corregir el diseño, es necesario tener acceso a Internet. |
| `--clean <one or more paths to catalogs>` | **Novedad de la versión 15.3, opcional**: quita las versiones anteriores de los componentes de un diseño que se ha actualizado a una versión más reciente. |

| **Opciones de instalación avanzadas** | **Descripción** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcional**: identificador del canal correspondiente a la instancia que se va a instalar. Es necesario para el comando de instalación, y se omite para otros comandos si se especifica `--installPath`. |
| `--channelUri <uri>` | **Opcional**: el URI del manifiesto del canal. Si no se quiere efectuar actualizaciones, `--channelUri` puede apuntar a un archivo inexistente (por ejemplo, --channelUri C:\doesntExist.chman). Se puede usar para el comando de instalación; se ignora para los demás comandos. |
| `--installChannelUri <uri>` | **Opcional**: el URI del manifiesto del canal que se va a usar para la instalación. El URI especificado por `--channelUri`, que debe especificarse cuando se especifica `--installChannelUri`, se usa para detectar actualizaciones. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| `--installCatalogUri <uri>` | **Opcional**: el URI del manifiesto del catálogo que se va a usar para la instalación. Si se especifica, el administrador del canal intenta descargar el manifiesto del catálogo de este URI antes de usar el URI en el manifiesto del canal de instalación. Este parámetro se usa para admitir la instalación sin conexión, donde la caché de diseño se creará con el catálogo del producto que ya se ha descargado. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| `--productId <id>` | **Opcional**: el id. del producto de la instancia que se instalará. Se rellena previamente en condiciones normales de instalación. |
| `--wait` | **Opcional**: el proceso esperará hasta que la instalación se complete antes de devolver un código de salida. Esto es útil al automatizar las instalaciones donde es necesario esperar a que la instalación finalice para controlar el código de retorno de esa instalación. |
| `--locale <language-locale>` | **Opcional**: cambia el idioma para mostrar de la interfaz de usuario del instalador. La configuración se conservará. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--cache` | **Nuevo en 15.2, opcional**: si está presente, los paquetes se conservarán después de instalarse de cara a posteriores reparaciones. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `--nocache` | **Novedad de la versión 15.2, opcional**: si los hay, los paquetes se eliminan después de instalarlos o repararlos. Solo se descargarán de nuevo si es necesario y se volverán a eliminar después de su uso. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `--noUpdateInstaller` | **Novedad en 15.2, opcional**: si está presente, impide que el instalador se actualice automáticamente cuando se especifica el modo silencioso. El instalador producirá un error en el comando y devolverá un código de salida distinto de cero si se especifica noUpdateInstaller con el modo silencioso cuando se requiere una actualización del instalador. |
| `--noWeb` | **Novedad de la versión 15.3, opcional**: el programa de instalación ahora descarga de Internet cualquier contenido que se esté instalando.  Todo el contenido que se esté instalando debe estar disponible en un diseño sin conexión.  Si falta contenido del diseño, no se podrá realizar la instalación.  Para obtener más información, consulte [Implementación de una instalación de red](create-a-network-installation-of-visual-studio.md). |
| `--path <name>=<path>` | **Novedad en 15.7 (opcional)**: se utiliza para especificar las rutas de acceso de instalación personalizada para la instalación. Los nombre de ruta de acceso admitidos son uso compartido, caché e instalar. |
| `--path cache=<path>` | **Novedad en 15.7 (opcional)**: utiliza la ubicación que especifique para descargar los archivos de instalación. Esta ubicación solo puede establecerse la primera vez que se instala Visual Studio. Ejemplo: `--path cache="C:\VS\cache"` |
| `--path shared=<path>` | **Novedad en 15.7 (opcional)**: contiene los archivos compartidos para las instalaciones en paralelo de Visual Studio. Algunas herramientas y SDK se instalan en una ubicación en esta unidad, mientras que otros pueden invalidar esta configuración e instalarse en otra unidad. Ejemplo: `--path shared="C:\VS\shared"` <br><br>Importante: Solo se puede establecer una vez y tiene que ser la primera vez que se instala Visual Studio. |
| `--path install=<path>` | **Novedad en 15.7 (opcional)**: equivalente a `–-installPath`. En particular, `--installPath "C:\VS"` y `--path install="C:\VS"` son equivalentes. Solo se puede usar uno de los dos a la vez. |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista de los id. de carga de trabajo y los id. de componente

Para obtener una lista de los identificadores de componente y carga de trabajo ordenados por producto de Visual Studio, vea la página [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma

| **Idioma-configuración regional** | **Idioma** |
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

| **Valor** | **Resultado** |
| --------- | ---------- |
| 0 | Operación completada correctamente |
| 1602 | Operación cancelada |
| 3010 | Operación completada correctamente, pero la instalación requiere reiniciar el equipo para que se pueda usar |
| 5004 | Operación cancelada |
| 5007 | Operación bloqueada: el equipo no cumple los requisitos |
| Otros | Condición de error: consulte los registros para obtener más información |

Cada operación genera varios archivos de registro en el directorio `%TEMP%` que indican el progreso de la instalación. Ordene la carpeta por fecha y busque los archivos que empiecen por `dd_bootstrapper`, `dd_client` y `dd_setup` para el programa previo, la aplicación del instalador y el motor de configuración, respectivamente.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

- [Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio 2017](command-line-parameter-examples.md)
- [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
- [Automatizar la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
- [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md)