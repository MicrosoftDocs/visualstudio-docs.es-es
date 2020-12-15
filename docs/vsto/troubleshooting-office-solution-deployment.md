---
title: Solucionar problemas de implementación de soluciones de Office
description: Obtenga información acerca de cómo solucionar problemas comunes que pueden surgir al implementar soluciones de Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: troubleshooting
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- Office development in Visual Studio, troubleshooting
- deploying applications [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b70b03e8342564de828059d1a335f6347c19b5a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97522967"
---
# <a name="troubleshoot-office-solution-deployment"></a>Solucionar problemas de implementación de soluciones de Office
  Este tema contiene información sobre cómo solucionar problemas comunes que pueden surgir al implementar soluciones de Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="troubleshoot-office-solutions-by-using-the-event-viewer"></a>Solucionar problemas de soluciones de Office mediante el visor de eventos
 Puede usar el visor de eventos en Windows para ver todos los mensajes de error capturados por [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , cuando instale o desinstale soluciones de Office. Puede usar estos mensajes desde el registrador de eventos para resolver los problemas de instalación e implementación. Para obtener más información, vea [registro de eventos para soluciones de Office](../vsto/event-logging-for-office-solutions.md).

## <a name="change-the-assembly-name-causes-conflicts"></a>Cambiar el nombre de ensamblado produce conflictos
 Si cambia el valor del **nombre del ensamblado** en la página **aplicación** del **Diseñador de proyectos** después de haber implementado una solución, las herramientas de publicación modificarán el paquete de instalación para que tenga un archivo *Setup.exe* y dos manifiestos de implementación. Si implementa dos archivos de manifiesto, podrían producirse las siguientes condiciones:

- Si el usuario final instala ambas versiones, la aplicación cargará ambos complementos VSTO.

- Si el complemento VSTO se instaló antes de cambiar el nombre del ensamblado, el usuario final nunca recibirá actualizaciones.

  Para evitar estas condiciones, no cambie el valor de **nombre de ensamblado** de la solución después de implementar la solución.

## <a name="check-for-updates-takes-a-long-time"></a>La comprobación de actualizaciones tarda mucho tiempo
 Visual Studio 2010 Tools para Office Runtime proporciona una entrada del registro que los administradores pueden usar para establecer el valor de tiempo de espera para descargar los manifiestos y la solución.

#### <a name="to-set-the-time-out-value"></a>Para establecer el valor de tiempo de espera

1. En el registro, navegue a la clave siguiente:

     **HKEY_CURRENT_USER\Software\Microsoft\VSTA**

2. En la subclave **AddInTimeout** , establezca el valor de tiempo de espera en milisegundos.

     Si la subclave **AddInTimeout** no existe, créela como DWORD.

## <a name="cant-update-or-publish-to-a-network-file-share"></a>No se puede actualizar ni publicar en un recurso compartido de archivos de red
 Las soluciones de Office que se encuentran en un recurso compartido de archivos de red pueden mostrar un mensaje engañoso durante las actualizaciones si el archivo de *Setup.exe* de la solución está bloqueado en un proceso mientras se publica la actualización. El mensaje podría decir lo siguiente: "No se puede agregar 'setup.exe' al sitio web. Ya existe un archivo 'setup.exe' en este sitio web."

 Para ayudar a evitar el bloqueo de archivos, puede hacer el recurso compartido de solo lectura a los usuarios finales. Sin embargo, si los documentos se encuentran en el recurso compartido, también serán de solo lectura para los usuarios finales.

## <a name="prerequisites-for-microsoft-office-arent-installed"></a>Los requisitos previos para Microsoft Office no están instalados
 Puede agregar .NET Framework, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]y los ensamblados de Office de interoperabilidad primarios al paquete de instalación como requisitos previos que se implementan con la solución de Office. Para obtener información sobre cómo instalar los ensamblados de interoperabilidad primarios, vea [configurar un equipo para desarrollar soluciones de Office](../vsto/configuring-a-computer-to-develop-office-solutions.md) y [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

## <a name="publish-using-localhost-can-cause-installation-problems"></a>La publicación con localhost puede causar problemas de instalación
 Cuando se usa `http://localhost` como ubicación de publicación o de instalación para las soluciones de nivel de documento, el **Asistente para publicación** no convierte la cadena en el nombre de equipo real. En este caso, la solución debe instalarse en el equipo de desarrollo. Para que las soluciones implementadas usen IIS en el equipo de desarrollo, use el nombre completo para todas las ubicaciones HTTP/HTTPS/FTP en lugar de localhost.

## <a name="cached-assemblies-are-loaded-instead-of-updated-assemblies"></a>Los ensamblados almacenados en caché se cargan en lugar de los ensamblados actualizados
 Fusion, el cargador de ensamblados de .NET Framework, carga la copia en caché de los ensamblados cuando la ruta de acceso de salida del proyecto se encuentra en un recurso compartido de red, el ensamblado se firma con un nombre seguro y no cambia la versión del ensamblado de la personalización. Si actualiza un ensamblado que cumple estas condiciones, la actualización no aparecerá la próxima vez que se ejecute el proyecto, ya que se carga la copia en caché.

 Puede configurar Visual Studio para que Fusion descargue los ensamblados cada vez que se ejecute el proyecto.

### <a name="to-download-assemblies-instead-of-loading-cached-copies"></a>Para descargar los ensamblados en lugar de cargar las copias en caché

1. En la barra de menús, elija **Proyecto**, _NombreDeProyecto_**Propiedades**.

2. En la página **Aplicación** , elija **Información de ensamblado**.

3. Establezca el número de revisión, el tercer campo, de la **versión del ensamblado** en un carácter comodín ( \* ). Por ejemplo, "1,0. *".  A continuación, elija el botón **Aceptar** .

   Después de cambiar la versión del ensamblado, puede continuar para firmar el ensamblado con un nombre seguro y Fusion cargará la versión más reciente de la personalización.

 [!NOTE]
> A partir de Visual Studio 2017, si intenta usar caracteres comodín en la versión de ensamblado, se producirá un error de compilación.  Esto se debe a que las comodines en la versión de ensamblado interrumpirán la característica de MSBuild determinista. Se le indicará que quite los caracteres comodín de la versión del ensamblado o deshabilite el determinismo.  Para obtener más información acerca de la característica determinista, vea: [propiedades comunes del proyecto de MSBuild](../msbuild/common-msbuild-project-properties.md) y [personalizar la compilación](../msbuild/customize-your-build.md)

## <a name="installation-fails-when-the-uri-has-characters-that-arent-us-ascii"></a>Se produce un error en la instalación cuando el identificador URI tiene caracteres que no son US-ASCII
 Al publicar una solución de Office en una ubicación HTTP/HTTPS/FTP, la ruta de acceso no puede tener caracteres Unicode que no estén en US-ASCII. Estos caracteres pueden producir un comportamiento incoherente en el programa de instalación. Utilice los caracteres US-ASCII para la ruta de instalación.

## <a name="prompt-to-manually-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>La solicitud de desinstalación manual aparece al publicar e instalar una solución en el equipo de desarrollo.
 Al compilar una solución de Office, la versión generada se registra automáticamente. Si previamente ha publicado e instalado la misma solución en el equipo de desarrollo, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] detecta que la ruta de instalación para la versión publicada y la versión generada son diferentes después de que la solución se compile, se vuelva a compilar o se publique. El mensaje de error dice: "No se puede instalar la personalización hay instalada otra versión y no se puede actualizar desde esta ubicación". Las claves del registro se actualizan cada vez que se vuelve a compilar una solución. Por lo tanto, debe desinstalar la versión anterior antes de publicar, depurar o ejecutar la nueva versión.

 Para evitar que aparezca el mensaje, cree otra cuenta de usuario en el equipo de desarrollo para probar la implementación. Como alternativa, puede desinstalar la versión de la lista de programas instalados en el equipo antes de publicar, depurar o volver a compilar la solución.

## <a name="uncaught-exception-or-method-not-found-error-when-you-install-a-solution"></a>Excepción no detectada o error de método no encontrado al instalar una solución
 Al instalar soluciones de Office abriendo el manifiesto de implementación (archivo *. VSTO* ), aplicación de Office, documento o libro, pueden aparecer mensajes de error para las siguientes condiciones:

- Método no encontrado.

- MissingMethodException.

- Excepción no detectada.

  Para evitar estos mensajes de error, instale la solución ejecutando el programa de instalación.

  Al instalar la solución sin ejecutar el programa de instalación, el instalador no busca ni instalar los requisitos previos. El programa de instalación comprueba la versión correcta de los requisitos previos y los instala según sea necesario.

## <a name="manifest-registry-keys-for-add-ins-change-after-an-installshield-limited-edition-project-is-built"></a>Las claves del registro de manifiesto para los complementos cambian una vez compilado un proyecto de InstallShield Limited Edition
 La clave del registro del manifiesto que forma parte de un programa de instalación del complemento de VSTO a veces cambia de *. VSTO* a *. dll. manifest* al compilar un proyecto de InstallShield Limited Edition.

 Para evitar este problema, cree el proyecto de InstallShield Limited Edition en una solución distinta o use CompanyName.AddinName como el valor de la clave del registro que contiene el nombre del complemento de VSTO.

## <a name="the-clickonce-installer-for-your-office-solution-doesnt-install-the-primary-interop-assemblies"></a>El instalador de ClickOnce para la solución de Office no instala los ensamblados de interoperabilidad primarios
 Al ejecutar el programa de instalación que crea ClickOnce para la solución de Office, el programa de instalación para los ensamblados de interoperabilidad primarios (PIA) de Office solo se ejecuta si hay ensamblados ya instalados.

 Si el programa de instalación no instala los PIA correctamente, instálelos manualmente ejecutando el archivo del instalador que se denomina *o2007pia.msi* desde el directorio de instalación.

## <a name="reinstall-office-solutions-causes-an-argument-out-of-range-exception"></a>La reinstalación de soluciones de Office produce una excepción de argumento fuera de intervalo
 Cuando vuelva a instalar una solución de Office, puede aparecer una excepción <xref:System.ArgumentOutOfRangeException> con el siguiente mensaje de error: El argumento especificado está fuera del intervalo de valores válidos.

 Esta situación se produce si las mayúsculas y minúsculas de la dirección URL de la ubicación de instalación son diferentes. Por ejemplo, este error aparece si instaló una solución de Office desde `http://fabrikam.com/ExcelSolution.vsto` la primera vez y, a continuación, se usa `http://fabrikam.com/excelsolution.vsto` la segunda vez.

 Para evitar que aparezca el mensaje, use la misma grafía al instalar soluciones de Office.

## <a name="cant-install-a-clickonce-solution-by-opening-the-deployment-manifest-from-the-web"></a>No se puede instalar una solución ClickOnce abriendo el manifiesto de implementación desde la web
 Los usuarios pueden instalar una solución de Office abriendo el manifiesto de implementación desde la Web. Sin embargo, algunas instalaciones de Internet Information Services (IIS) bloquean la extensión de nombre de archivo *. VSTO* . Debe definir el tipo MIME en IIS antes de usarlo para implementar una solución de Office.

 Para obtener información sobre cómo definir el tipo MIME en IIS 7, vea [Agregar un tipo MIME (IIS7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725608(v=ws.10)).

 Establezca la extensión en **.vsto** y el tipo MIME en **application/x-ms-vsto**.

## <a name="see-also"></a>Consulte también

- [Solución de problemas de implementaciones de ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Solucionar problemas de Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)