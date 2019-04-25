---
title: Problemas de seguridad, control de versiones y manifiestos en implementaciones de ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
ms.assetid: d5d0c90b-ac1a-44e2-88dc-0d0ffd881624
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e971271d17c88780ec543ffc12ed4c6ebcc48f23
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60043685"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemas de seguridad, versiones y manifiestos en implementaciones de ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hay una variedad de problemas con [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] seguridad, versiones de las aplicaciones y manifiestos sintaxis y semántica que puede causar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación se realice correctamente.  
  
## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce y Control de cuentas de usuario de Windows Vista  
 En [!INCLUDE[windowsver](../includes/windowsver-md.md)], las aplicaciones de forma predeterminada se ejecutan como usuario estándar, incluso si el usuario actual ha iniciado sesión con una cuenta que tenga permisos de administrador. Si una aplicación debe realizar una acción que requiere permisos de administrador, indica al sistema operativo, que, a continuación, pide al usuario que escriba sus credenciales de administrador. Esta característica, que se denomina Control de cuentas de usuario (UAC), impide que las aplicaciones realicen cambios que pueden afectar a todo el sistema operativo sin la aprobación explícita de un usuario. Aplicaciones Windows declaran que requieren esta elevación de permisos especificando el `requestedExecutionLevel` atributo en la `trustInfo` sección de su manifiesto de aplicación.  
  
 Debido al riesgo de exposición de las aplicaciones a ataques de elevación de seguridad, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicaciones no pueden solicitar la elevación de permisos si UAC está habilitado para el cliente. Cualquier [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación que intenta establecer su `requestedExecutionLevel` atributo `requireAdministrator` o `highestAvailable` no se instalará en [!INCLUDE[windowsver](../includes/windowsver-md.md)].  
  
 En algunos casos, su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación podría intentar ejecutar con permisos de administrador debido a la lógica de detección del instalador en [!INCLUDE[windowsver](../includes/windowsver-md.md)]. En este caso, puede establecer el `requestedExecutionLevel` atributo en el manifiesto de aplicación para `asInvoker`. Esto hará que la aplicación se ejecute sin la elevación. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Este atributo se agrega automáticamente a todos los manifiestos de aplicación.  
  
 Si está desarrollando una aplicación que requiere permisos de administrador para toda la duración de la aplicación, considere la posibilidad de implementar la aplicación mediante la tecnología de Windows Installer (MSI) en su lugar. Para obtener más información, consulte [conceptos básicos de Windows Installer](../extensibility/internals/windows-installer-basics.md).  
  
## <a name="online-application-quotas-and-partial-trust-applications"></a>Aplicaciones de confianza parcial y las cuotas de la aplicación en línea  
 Si su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación se ejecuta en línea en lugar de a través de una instalación, deben ajustarse a la cuota que se reservan para las aplicaciones en línea. Además, una aplicación de red que se ejecuta en confianza parcial, como un conjunto restringido de permisos de seguridad, no puede ser mayor que la mitad del tamaño de cuota.  
  
 Para más información e instrucciones sobre cómo cambiar la cuota de aplicaciones en línea, consulte [información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).  
  
## <a name="versioning-issues"></a>Problemas de versiones  
 Puede experimentar problemas si incrementa el número de versión del ensamblado para reflejar la actualización de la aplicación y asigne nombres seguros al ensamblado. Cualquier ensamblado compilado con una referencia a un ensamblado con nombre seguro debe compilarse por sí o el ensamblado intentará hacer referencia a la versión anterior. El ensamblado intentará esto porque el ensamblado está utilizando el valor de la versión anterior en su solicitud de enlace.  
  
 Por ejemplo, supongamos que tiene un ensamblado con nombre seguro en su propio proyecto con la versión 1.0.0.0. Después de compilar el ensamblado, agregarlo como una referencia al proyecto que contiene la aplicación principal. Si actualiza el ensamblado, incrementa la versión a 1.0.0.1 y vuelva a implementarlo sin volver a compilar también la aplicación, la aplicación no podrá cargar el ensamblado en tiempo de ejecución.  
  
 Este error puede producirse solo si está editando su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiestos manualmente; no deberían experimentar este error si se genera la implementación mediante [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)].  
  
## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Especificar ensamblados individuales de .NET Framework en el manifiesto  
 La aplicación no se cargará si ha editado manualmente un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implementación para hacer referencia a una versión anterior de un [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ensamblado. Por ejemplo, si ha agregado una referencia al ensamblado System.Net para una versión de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] antes de la versión especificada en el manifiesto, a continuación, se producirá un error. En general, no debe intentar especificar referencias a persona [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ensamblados, como la versión de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] contra la que se ejecuta la aplicación se especifica como una dependencia en el manifiesto de aplicación.  
  
## <a name="manifest-parsing-issues"></a>Existen problemas de análisis de manifiestos  
 Los archivos de manifiesto que se usan por [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] son archivos XML, y deben ser correcto y válido: deben cumplir las reglas de sintaxis XML y usar solo los elementos y atributos definidos en el esquema XML correspondiente.  
  
 Algo que puede causar problemas en un archivo de manifiesto es seleccionar un nombre para la aplicación que contiene un carácter especial, como una comilla simple o doble. Nombre de la aplicación forma parte de su [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] identidad. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] actualmente no se analiza las identidades que contienen caracteres especiales. Si no se puede activar la aplicación, asegúrese de que se utilizan caracteres numéricos y alfabéticos solo para el nombre y, intente implementar de nuevo.  
  
 Si ha editado manualmente los manifiestos de implementación o aplicación, se pueden haberlos dañado involuntariamente. Un manifiesto dañado evitará una correcta [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalación. Puede depurar estos errores en tiempo de ejecución, haga clic en **detalles** en el **ClickOnce Error** cuadro de diálogo y leer el mensaje de error en el registro. El registro mostrará uno de los mensajes siguientes:  
  
- Una descripción del error de sintaxis y el número de línea y el carácter posición donde se produjo el error.  
  
- El nombre de un elemento o atributo que se usa infringe el esquema del manifiesto. Si ha agregado manualmente XML a los manifiestos, tendrá que comparar las adiciones a los esquemas del manifiesto. Para obtener más información, consulte [del manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) y [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md).  
  
- Un conflicto de identificador. Las referencias de dependencias en los manifiestos de implementación y las aplicaciones deben ser únicas en ambos sus `name` y `publicKeyToken` atributos. Si ambos atributos coinciden entre dos elementos cualesquiera dentro de un manifiesto, análisis del manifiesto no se realizará correctamente.  
  
## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauciones al cambiar manualmente los manifiestos o aplicaciones  
 Cuando se actualiza un manifiesto de aplicación, deberá volver a firmar el manifiesto de aplicación y el manifiesto de implementación. El manifiesto de implementación contiene una referencia al manifiesto de aplicación que incluye el hash de ese archivo y su firma digital.  
  
### <a name="precautions-with-deployment-provider-usage"></a>Precauciones con el uso del proveedor de implementación  
 El [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifiesto de implementación tiene un `deploymentProvider` propiedad que señala a la ruta de acceso completa de la ubicación desde donde se debería instalar y atiende la aplicación:  
  
```  
<deploymentProvider codebase="http://myserver/myapp.application" />  
```  
  
 Esta ruta de acceso se establece cuando [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] crea la aplicación y es obligatoria para las aplicaciones instaladas. La ruta de acceso apunta a la ubicación estándar donde la [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] instalador instalará la aplicación y buscar actualizaciones. Si usas el **xcopy** comando para copiar un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicación a una ubicación diferente, pero no cambian el `deploymentProvider` propiedad, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] todavía hará referencia a la ubicación original cuando intenta descargar la aplicación.  
  
 Si desea mover o copiar una aplicación, también debe actualizar el `deploymentProvider` ruta de acceso, por lo que realmente instala el cliente de la nueva ubicación. La actualización de esta ruta de acceso es principalmente un problema si ha instalado las aplicaciones. Para las aplicaciones en línea que siempre se inician a través de la dirección URL original, establecer el `deploymentProvider` es opcional. Si `deploymentProvider` está establecido, se respetará; en caso contrario, se usará la dirección URL utilizada para iniciar la aplicación como la dirección URL base para descargar los archivos de la aplicación.  
  
> [!NOTE]
>  Cada vez que actualice el manifiesto debe también firmarlo de nuevo.  
  
## <a name="see-also"></a>Vea también  
 [Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)   
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
