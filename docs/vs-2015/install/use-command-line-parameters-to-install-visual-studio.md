---
title: Uso de parámetros de la línea de comandos para instalar Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: cd61d03b5639038612e305697f4245e582ee3efe
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794044"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Usar parámetros de la línea de comandos para instalar Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para consultar la documentación más reciente sobre Visual Studio 2017, vea [Uso de parámetros de la línea de comandos para instalar Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Al instalar Visual Studio 2015 desde un símbolo del sistema, puede usar los siguientes parámetros de línea de comandos, también conocidos como modificadores.

> [!NOTE]
>  Asegúrese de que use el programa de instalación real y no el archivo de programa previo. Por ejemplo, asegúrese de utilizar **`vs_enterprise.exe`** en lugar de vs_enterprise_*GUID*.exe. Puede descargar un instalador de [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015).

## <a name="list-of-command-line-parameters"></a>Lista de parámetros de la línea de comandos
 Los parámetros de la línea de comandos de Visual Studio no distinguen mayúsculas de minúsculas.

|Parámetro|Descripción|
|---------------|-----------------|
|**/?**<br /><br /> **/help**<br /><br /> **/h**|Muestra los parámetros de la línea de comandos.|
|**/AddRemoveFeatures**|Especifica qué características se van a agregar o quitar del producto instalado.|
|**/AdminFile** *AdminDeployment.xml*|Instala Visual Studio usando el archivo de datos que especificó para la instalación administrativa.|
|**/ChainingPackage** *BundleName*|Especifica qué agrupación está encadenando este paquete. También puede usarse para especificar una cohorte para la experiencia de mejora del cliente.|
|**/CreateAdminFile \<filename>**|Especifica la ubicación para crear un archivo de control que se puede usar con /AdminFile|
|**/CustomInstallPath** *InstallationDirectory*|Instala todos los paquetes que se pueden volver a establecer como destino en el directorio especificado.|
|**/ForceRestart**|Reinicia siempre el equipo después de la instalación.|
|**/full**|Instala todas las características del producto.|
|**/Installselectableitems \<nombre del elemento 1 > [;\< nombre del elemento 2 >]**|Lista de elementos del árbol de selección que se comprueba en la pantalla de selección del Asistente para la instalación.|
|**/l**<br /><br /> **/ Iniciar sesión** *nombre de archivo*|Especifica una ubicación para el archivo de registro.|
|**/ Layout** *directorio*|Copia los archivos del disco de instalación al directorio especificado.|
|**/NoCacheOnlyMode**|Impide que se rellene automáticamente la memoria caché del paquete.|
|**/NoRefresh**|Impide comprobar la existencia de versiones más recientes de este producto para versiones actualizadas necesarias o recomendadas.|
|**/norestart**|Impide que la aplicación de instalación reinicie el equipo durante o después de la instalación. Vea la sección Códigos de retorno de la [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md) para buscar los códigos de retorno.|
|**/noweb**|Impide la instalación desde Internet.|
|**/Overridefeeduri \<ruta de acceso al archivo de fuente >**|Ruta de acceso a una fuente local y externa que describe los elementos de software|
|**/ProductKey**<br /><br /> *ProductKey*|Establece una clave del producto personalizada que no contiene ningún guion y no tiene más de 25 caracteres.|
|**/PromptRestart**|Pregunta al usuario antes de reiniciar el equipo.|
|**/q**<br /><br /> **/quiet**<br /><br /> **/s**<br /><br /> **/silent**|Suprime la interfaz de usuario (IU) para la aplicación de instalación. Si Visual Studio ya está instalado y no especifica ningún parámetro excepto este, la aplicación de instalación se ejecuta en modo de mantenimiento.|
|**/qb**<br /><br /> **/passive**|Muestra el progreso pero no espera datos proporcionados por el usuario.|
|**/repair**|Repara Visual Studio.|
|**/SuppressRefreshPrompt**|Evita mostrar que el cuadro de diálogo de actualización disponible en el Asistente para la instalación, de modo que el Asistente para la instalación aceptará automáticamente cualquier versión actualizada necesaria o recomendada.|
|**/u**<br /><br /> **/uninstall**|Desinstala [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|
|**/Uninstall/Force**<br /><br /> **/u /force**|Desinstala Visual Studio y todas las características que se comparten con otros productos. **Advertencia:** si usa este parámetro, otros productos que están instalados en el mismo equipo podrían dejar de funcionar correctamente.|

## <a name="see-also"></a>Vea también
 [Guía del administrador de Visual Studio](../install/visual-studio-administrator-guide.md)