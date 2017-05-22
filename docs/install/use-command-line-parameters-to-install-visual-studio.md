---
title: "Usar parámetros de la línea de comandos para instalar Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
author: TerryGLee
ms.author: tglee
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
ms.sourcegitcommit: b5b496e0de0a12c9f52c944ef9e768c82d9be783
ms.openlocfilehash: 429d55b3d0050eb0743d4abf39c202ad1b8383b1
ms.contentlocale: es-es
ms.lasthandoff: 05/08/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017"></a>Uso de parámetros de la línea de comandos para instalar Visual Studio 2017
Cuando instala Visual Studio 2017 desde un símbolo del sistema, puede usar diversos parámetros de la línea de comandos para controlar o personalizar la instalación. Desde la línea de comandos, puede hacer lo siguiente:

- Iniciar la instalación con determinadas opciones preseleccionadas.
- Automatizar el proceso de instalación.
- Crear una caché (diseño) de los archivos de instalación para su uso posterior.

Las opciones de la línea de comandos se usan junto con el programa previo de instalación, que es el archivo pequeño (de aproximadamente 1 MB) que inicia el proceso de descarga. El programa previo es el primer ejecutable que se inicia cuando se realiza la descarga desde el sitio de Visual Studio. Mediante estos vínculos puede ir directamente a la versión más reciente del programa previo para la edición del producto que está instalando:

* [Visual Studio 2017 Enterprise](https://aka.ms/vs/15/release/vs_enterprise.exe)
* [Visual Studio 2017 Professional](https://aka.ms/vs/15/release/vs_professional.exe)
* [Visual Studio 2017 Community](https://aka.ms/vs/15/release/vs_community.exe)

## <a name="list-of-command-line-parameters"></a>Lista de parámetros de la línea de comandos  
 Los parámetros de la línea de comandos de Visual Studio no distinguen mayúsculas de minúsculas.

> Sintaxis: `vs_enterprise.exe [command] <options>...`

(Reemplace `vs_enterprise.exe` según corresponda para la edición del producto que está instalando. Para obtener ejemplos, consulte la página [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)).

| **Comando** | **Descripción** |
| ----------------------- | --------------- |
| (en blanco) | Instala el producto. |
| `modify` | Modifica un producto instalado. |
| `update` | Actualiza un producto instalado. |
| `repair` | Repara un producto instalado. |
| `uninstall` | Desinstala un producto instalado. |

| **Opción de instalación** | **Descripción** |
| ----------------------- | --------------- |
| `--installPath <dir>` | El directorio de instalación en el que actuará la instancia. Para el comando de instalación, es **opcional** y es el lugar donde se instalará la instancia. Para otros comandos, es **obligatorio** y es el lugar donde se instaló la instancia instalada anteriormente. |
| `--addProductLang <language-locale>` | **Opcional**: durante una operación de instalación o modificación, determina los paquetes de idioma de la interfaz de usuario que se van a instalar con el producto. Puede aparecer varias veces en la línea de comandos para agregar varios paquetes de idioma. Si no está presente, la instalación usará la configuración regional del equipo. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--removeProductLang <language-locale>` | **Opcional**: durante una operación de instalación o modificación, determina los paquetes de idioma de la interfaz de usuario que se van a quitar del producto. Puede aparecer varias veces en la línea de comandos para agregar varios paquetes de idioma. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante `--includeRecommended` o `--includeOptional`. Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeRecommended;includeOptional`). Para obtener más información, consulte nuestra página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md).|
| `--remove <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para quitar. Para obtener más información, consulte nuestra página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md).|
| `--in <path>` | **Opcional**: el URI o la ruta de acceso de un archivo de respuesta.  |
| `--all` | **Opcional**: si se instalan o no todas las cargas de trabajo y componentes para un producto. |
| `--allWorkloads` | **Opcional**: instala todas las cargas de trabajo y sus componentes obligatorios, no se instalan los componentes recomendados ni opcionales. |
| `--includeRecommended` | **Opcional**: incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: incluye los componentes opcionales para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`.  |
| `--quiet, -q` | **Opcional**: no muestra ninguna interfaz de usuario al realizar la instalación. |
| `--passive, -p` | **Opcional**: muestra la interfaz de usuario, pero no solicita ninguna interacción del usuario. |
| `--norestart` | **Opcional**: si está presente, los comandos con `--passive` o `--quiet` no reiniciarán automáticamente la máquina (si es necesario). Se omite si no se especifica `--passive` ni `--quiet`.  |
| `--nickname <name>` | **Opcional**: esto define el alias que se va a asignar a un producto instalado. El alias no puede tener más de 10 caracteres.  |
| `--productKey` | **Opcional**: esto define la clave del producto que se va a usar para un producto instalado. Se compone de 25 caracteres alfanuméricos en formato `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx` o `xxxxxxxxxxxxxxxxxxxxxxxxx`. |
| `--help, --?, -h, -?` | Muestra una versión sin conexión de esta página. |

> Nota: Al especificar varias cargas de trabajo y componentes, debe repetir el modificador de la línea de comandos `--add` o `--remove` para cada elemento.

| **Opciones de diseño** | **Descripción** |
| ----------------------- | --------------- |
| `--layout <dir>` | Especifica un directorio para crear una caché de instalación sin conexión. Para más información, consulte [Create an offline installation of Visual Studio 2017](create-a-network-installation-of-visual-studio.md) (Creación de una instalación sin conexión de Visual Studio 2017).|
| `--lang <one or more language-locales>` | **Opcional**: se usa con `--layout` para preparar una caché de instalación sin conexión con paquetes de recursos con los idiomas especificados. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--add <one or more workload or component IDs>` | **Opcional**: uno o varios identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante `--includeRecommended` o `--includeOptional`. Para un control más preciso, puede anexar `;includeRecommended` o `;includeOptional` al identificador (por ejemplo, `--add Workload1;includeRecommended` o `--add Workload2;includeOptional`). Para obtener más información, consulte nuestra página [Identificadores de componente y carga de trabajo](workload-and-component-ids.md). <br/>**Nota**: Si se usa `--add`, solo se descargan las cargas de trabajo y los componentes especificados y sus dependencias. Si no se especifica `--add`, todos los componentes y las cargas de trabajo se descargarán en el diseño.|
| `--includeRecommended` | **Opcional**: incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con `--allWorkloads` o `--add`. |
| `--includeOptional` | **Opcional**: incluye los componentes recomendados *y* opcionales para las cargas de trabajo que se incluyen en el diseño. Las cargas de trabajo se especifican con `--add`.  |


| **Opciones de instalación avanzadas** | **Descripción** |
| ----------------------- | --------------- |
| `--channelId <id>` | **Opcional**: el identificador del canal de la instancia que se instalará. Es necesario para el comando de instalación, y se omite para otros comandos si se especifica `--installPath`. |
| `--channelUri <uri>` | **Opcional**: el URI del manifiesto del canal. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| `--installChannelUri <uri>` | **Opcional**: el URI del manifiesto del canal que se va a usar para la instalación. El URI especificado por `--channelUri` (que debe especificarse cuando se especifica `--installChannelUri`) se usará para detectar actualizaciones. Si no se quieren actualizaciones, `--channelUri` debe especificarse sin un argumento. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| `--installCatalogUri <uri>` | **Opcional**: el URI del manifiesto del catálogo que se va a usar para la instalación. Si se especifica, el administrador del canal intentará descargar el manifiesto del catálogo de este URI antes de usar el URI en el manifiesto del canal de instalación. Este parámetro se usa para admitir la instalación sin conexión, donde la caché de diseño se creará con el catálogo del producto que ya se ha descargado. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| `--productId <id>` | **Opcional**: el id. del producto de la instancia que se instalará. Se rellena previamente en condiciones normales de instalación. |
| `--wait` | **Opcional**: el proceso esperará hasta que la instalación se complete antes de devolver un código de salida. Esto es útil al automatizar las instalaciones donde es necesario esperar a que la instalación finalice para controlar el código de retorno de esa instalación. |
| `--locale <language-locale>` | **Opcional**: cambia el idioma para mostrar de la interfaz de usuario del instalador. La configuración se conservará. Para obtener más información, consulte la sección [Lista de configuraciones regionales de idioma](#list-of-language-locales) de esta página.|
| `--cache` | **Nuevo en 15.2, opcional**: si está presente, los paquetes se conservarán después de instalarse de cara a posteriores reparaciones. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |
| `--nocache` | **Nuevo en 15,2, opcional**: si está presente, los paquetes se eliminarán después de instalarse o repararse. Solo se descargarán de nuevo si es necesario y se volverán a eliminar después de su uso. Esta opción invalida la configuración global de directiva que se usará en posteriores instalaciones, reparaciones o modificaciones. La directiva predeterminada es almacenar en caché los paquetes. Se omite para el comando de desinstalación. Para más información, lea cómo [deshabilitar o mover la caché de paquetes](disable-or-move-the-package-cache.md). |

## <a name="list-of-workload-ids-and-component-ids"></a>Lista de los id. de carga de trabajo y los id. de componente
Para obtener una lista de los identificadores de componente y carga de trabajo ordenados por producto de Visual Studio, vea la página [Identificadores de componente y carga de trabajo de Visual Studio 2017](workload-and-component-ids.md).

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma
| **Idioma-configuración regional** | **Idioma** |
| ----------------------- | --------------- |
| cs-CZ | Checo |
| de-DE | Alemán |
| en-US | Inglés |
| es-ES | Español |
| fr-FR | Francés |
| it-IT | Italiano |
| ja-JP | Japonés |
| ko-KR | Coreano |
| pl-PL | Polaco |
| pt-BR | Portugués (Brasil) |
| ru-RU | Ruso |
| tr-TR | Turco |
| zh-CN | Chino (simplificado) |
| zh-TW | Chino (tradicional) |

## <a name="error-codes"></a>Códigos de error
En función del resultado de la operación, la variable de entorno `%ERRORLEVEL%` se establecerá en uno de los valores siguientes:

| **Valor** | **Resultado** |
| --------- | ---------- |
| 0 | Operación completada correctamente |
| 3010 | Operación completada correctamente, pero la instalación requiere reiniciar el equipo para que se pueda usar |
| Otros | Condición de error: consulte los registros para obtener más información |

Cada operación generará varios archivos de registro en el directorio `%TEMP%` que indican el progreso de la instalación. Ordene la carpeta por fecha y busque los archivos que empiecen por `dd_bootstrapper`, `dd_client` y `dd_setup` para el programa previo, la aplicación del instalador y el motor de configuración, respectivamente.

## <a name="see-also"></a>Vea también

 * [Instalación de Visual Studio 2017](install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
 * [Ejemplos de parámetros de línea de comandos para la instalación de Visual Studio 2017](command-line-parameter-examples.md)
 * [Automatizar la instalación de Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
 * [Notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

