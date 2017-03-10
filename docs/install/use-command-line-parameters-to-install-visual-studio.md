---
title: "Usar parámetros de la línea de comandos para instalar Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
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
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 18a3d03663ac96e0751d4a420244b835be7146bf
ms.lasthandoff: 02/22/2017

---
# <a name="use-command-line-parameters-to-install-visual-studio-2017-rc"></a>Usar parámetros de la línea de comandos para instalar Visual Studio 2017 RC
Cuando instale Visual Studio 2017 RC desde un símbolo del sistema, puede usar los siguientes parámetros de línea de comandos (también conocidos como modificadores).  

## <a name="list-of-command-line-parameters"></a>Lista de parámetros de la línea de comandos  
 Los parámetros de la línea de comandos de Visual Studio no distinguen mayúsculas de minúsculas.  

| **Comando de línea de comandos** | **Descripción** |
| ----------------------- | --------------- |  
| ```modify``` | Modifica un producto instalado. |
| ```update``` | Actualiza un producto instalado. |
| ```repair``` | Repara un producto instalado. |
| ```uninstall``` | Desinstala un producto instalado. |

Si no se especifica ningún comando, instalará el producto.

| **Opción de la línea de comandos** | **Descripción** |
| ----------------------- | --------------- |  
| ```--installPath <dir>``` | El directorio de instalación en el que actuará la instancia. Para el comando de instalación, este es el lugar donde se instalará la instancia. Para otros comandos, este es el lugar donde se ha instalado la instancia instalada anteriormente. |
| ```--productId <id>``` | El id. del producto de la instancia que se instalará. Esto es necesario para el comando de instalación, y se omite para otros comandos si --installPath se especifica. |
| ```--layout <dir>``` | Opcional: Especifica un directorio para crear una caché de instalación sin conexión. Al seleccionar esta opción, se agregará también de forma implícita la opción "--wait". |
| ```--lang <language-locale>``` *[&#60;configuración regional de idioma&#62; ...]* | Opcional: Instalar o desinstalar paquetes de recursos con los idiomas especificados. |
| ```--add <workload or component ID>``` *[&#60;Id. de componente o carga de trabajo&#62; ...]* | Opcional: Uno o más identificadores de componente o carga de trabajo para agregar. Se instalan los componentes necesarios del artefacto, pero no los componentes recomendados ni opcionales. Puede controlar los componentes adicionales de forma global mediante "--includeRecommended" o "--includeOptional". Para un control preciso, puede anexar "; includeRecommended" o ";includeOptional" al artifactId (por ejemplo, "--add Workload1;includeRecommended" o "--add Workload2;includeOptional;includeRecommended"). |
| ```--remove <workload or component ID>``` *[&#60;Id. de componente o carga de trabajo&#62; ...]* | Opcional: Uno o más identificadores de componente o carga de trabajo para quitar. |
| ```--all``` | Opcional: Si se instalan o no todas las cargas de trabajo y componentes para un producto. |
| ```--allWorkloads``` | Opcional: Instala todas las cargas de trabajo y sus componentes necesarios, no se instalan los componentes recomendados ni opcionales. |
| ```--includeRecommended``` | Opcional: Incluye los componentes recomendados para cualquier carga de trabajo que se instale, pero no los componentes opcionales. Las cargas de trabajo se especifican con --allWorkloads o --add. |
| ```--includeOptional``` | Opcional: Incluye los componentes opcionales para cualquier carga de trabajo que se instale, pero no los componentes recomendados. Las cargas de trabajo se especifican con --allWorkloads o --add.  |
| ```--quiet, -q``` | Opcional: No muestra ninguna interfaz de usuario al realizar la instalación. |
| ```--passive, -p``` | Opcional: Muestra la interfaz de usuario, pero no solicita ninguna interacción del usuario. |
| ```--norestart``` | Opcional: Si está presente, los comandos con --passive o --quiet no reiniciarán automáticamente el equipo (si es necesario). Esto se ignora si --passive o --quiet se especifican.  |
| ```--locale <language-locale>``` | Opcional: Cambia el idioma para mostrar de la interfaz de usuario del instalador. La configuración se conservará. |
| ```--nickname <name>``` | Opcional: Esto define el alias que se va a asignar a un producto instalado. El alias no puede tener más de 10 caracteres.  |
| ```--help, --?, -h, -?``` | Mostrar uso de parámetros. |

>Nota: Al especificar varias cargas de trabajo y componentes, debe repetir el modificador de la línea de comandos `--add` o `--remove` para cada elemento.

| **Opción de la línea de comandos avanzada** | **Descripción** |
| ----------------------- | --------------- |  
| ```--channelId <id>``` | Opcional: El id. del canal de la instancia que se instalará. Esto es necesario para el comando de instalación, y se omite para otros comandos si --installPath se especifica. |
| ```--channelUri <uri>``` | Opcional: El URI del manifiesto del canal. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| ```--installChannelUri <uri>``` | Opcional: El URI del manifiesto del canal que se va a usar para la instalación. El URI especificado por --channelUri (que debe especificarse cuando --installChannelUri está especificado) se usará para detectar actualizaciones. Si no se quieren actualizaciones, --channelUri debe especificarse sin un argumento. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| ```--installCatalogUri <uri>``` | Opcional: El URI del manifiesto del catálogo que se va a usar para la instalación. Si se especifica, el administrador del canal intentará descargar el manifiesto del catálogo de este URI antes de usar el URI en el manifiesto del canal de instalación. Este parámetro se usa para admitir la instalación sin conexión, donde la caché de diseño se creará con el catálogo del producto que ya se ha descargado. Esto puede usarse para el comando de instalación; se ignora para los demás comandos. |
| ```--in <path>``` | Opcional: El URI o la ruta de acceso de un archivo de respuesta.  |
| ```--addProductLang <language-locale>``` | Opcional: Esto define el lenguaje de un artefacto (grupo, carga de trabajo o componente) que se va a instalar. Puede aparecer varias veces en la línea de comandos. Es opcional para los comandos de modificación e instalación, se ignora para los comandos de desinstalación, reparación y actualización. Si no está presente, la instalación usará la configuración regional del equipo. |
| ```--removeProductLang <language-locale>``` | Opcional: Esto define el lenguaje de un artefacto (grupo, carga de trabajo o componente) que se va a quitar. Puede aparecer varias veces en la línea de comandos. Es opcional para los comandos de modificación e instalación, se ignora para los comandos de desinstalación, reparación y actualización. |
| ```--wait``` | Opcional: El proceso esperará hasta que la instalación se complete antes de devolver un código de salida. Esto es útil al automatizar las instalaciones donde es necesario esperar a que la instalación finalice para controlar el código de retorno de esa instalación. |
| ```--productKey``` | Opcional: Esto define la clave del producto que se va a usar para un producto instalado. Se compone de 25 caracteres alfanuméricos en el formato "xxxxx-xxxxx-xxxxx-xxxxx-xxxxx" o "xxxxxxxxxxxxxxxxxxxxxxxxx". |
## <a name="list-of-workload-ids-and-component-ids"></a>Lista de los id. de carga de trabajo y los id. de componente
Para obtener una lista de los id. de componente y carga de trabajo ordenados por producto de Visual Studio, vea nuestra página [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (Identificadores de componente y carga de trabajo de Visual Studio 2017).

> [!WARNING]
> El parámetro --layout producirá un error si el nombre de archivo .exe de instalación incluye números. Para evitar este problema, debe quitar los números del nombre de archivo; por ejemplo, cambie el nombre *vs_community__198521760.1486960229.exe* por ***vs_community.exe***.

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma
| **Idioma-configuración regional** | **Idioma** |
| ----------------------- | --------------- |  
| cs-CZ | Checo |
| de-DE | Alemán |
| en-US | Inglés |
| es-ES | Español |
| cs-CZ | Checo |
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



> [!IMPORTANT]
> A pesar de que, en general, se admite el uso de Visual Studio 2017 RC en un entorno de producción, las cargas de trabajo y los componentes que aparecen marcados como "Versión preliminar" en la interfaz de usuario de instalación no son compatibles para usarlos en un entorno de producción.

## <a name="see-also"></a>Vea también

 * [Instalar Visual Studio](install-visual-studio.md)
 * [Crear una instalación sin conexión de Visual Studio 2017 RC](create-an-offline-installation-of-visual-studio.md)
 * [Notificar un problema con Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

