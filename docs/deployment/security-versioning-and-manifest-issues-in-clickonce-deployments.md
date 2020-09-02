---
title: Problemas de seguridad, control de versiones y manifiestos en la implementación de ClickOnce
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb2ec5229132265feb1095c9ee921d73a1568dd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "66745606"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Seguridad, control de versiones y manifiestos problemas en implementaciones de ClickOnce

Hay una gran variedad de problemas con la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] seguridad, el control de versiones de la aplicación y la sintaxis y la semántica del manifiesto que pueden hacer que una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación no se realice correctamente.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce y control de cuentas de usuario de Windows Vista

En [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] , las aplicaciones de se ejecutan de forma predeterminada como un usuario estándar, aunque el usuario actual inicie sesión con una cuenta que tenga permisos de administrador. Si una aplicación debe realizar una acción que requiere permisos de administrador, indica al sistema operativo que, a continuación, solicita al usuario que escriba sus credenciales de administrador. Esta característica, que se denomina control de cuentas de usuario (UAC), evita que las aplicaciones realicen cambios que pueden afectar a todo el sistema operativo sin la aprobación explícita de un usuario. Las aplicaciones de Windows declaran que requieren esta elevación de permisos especificando el `requestedExecutionLevel` atributo en la `trustInfo` sección del manifiesto de aplicación.

Debido al riesgo de exponer las aplicaciones a ataques de elevación de seguridad, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] las aplicaciones no pueden solicitar la elevación de permisos si UAC está habilitado para el cliente. Cualquier [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que intente establecer su `requestedExecutionLevel` atributo en `requireAdministrator` o `highestAvailable` no se instalará en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

En algunos casos, la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación puede intentar ejecutarse con permisos de administrador debido a la lógica de detección del instalador en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . En este caso, puede establecer el `requestedExecutionLevel` atributo en el manifiesto de aplicación en `asInvoker` . Esto hará que la aplicación se ejecute sin elevación. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] agrega automáticamente este atributo a todos los manifiestos de aplicación.

Si está desarrollando una aplicación que requiere permisos de administrador para toda la duración de la aplicación, considere la posibilidad de implementar la aplicación mediante la tecnología de Windows Installer (MSI). Para obtener más información, vea [conceptos básicos de Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Cuotas de aplicación en línea y aplicaciones de confianza parcial

Si la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecuta en línea en lugar de a través de una instalación, debe ajustarse a la cuota reservada para las aplicaciones en línea. Además, una aplicación de red que se ejecuta en confianza parcial, como con un conjunto restringido de permisos de seguridad, no puede ser mayor que la mitad del tamaño de la cuota.

Para obtener más información e instrucciones sobre cómo cambiar la cuota de aplicación en línea, vea [información general](../deployment/clickonce-cache-overview.md)sobre la caché de ClickOnce.

## <a name="versioning-issues"></a>Problemas de control de versiones

Puede experimentar problemas si asigna nombres seguros al ensamblado e incrementa el número de versión del ensamblado para reflejar una actualización de la aplicación. Los ensamblados compilados con una referencia a un ensamblado con nombre seguro deben volver a compilarse, o bien el ensamblado intentará hacer referencia a la versión anterior. El ensamblado lo probará porque el ensamblado usa el valor de la versión anterior en su solicitud de enlace.

Por ejemplo, supongamos que tiene un ensamblado con nombre seguro en su propio proyecto con la versión 1.0.0.0. Después de compilar el ensamblado, agréguelo como una referencia al proyecto que contiene la aplicación principal. Si actualiza el ensamblado, incrementa la versión a 1.0.0.1 e intenta implementarla sin volver a compilar la aplicación, la aplicación no podrá cargar el ensamblado en tiempo de ejecución.

Este error solo puede producirse si está editando los [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos manualmente; no debería experimentar este error si genera la implementación con Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Especificar ensamblados de .NET Framework individuales en el manifiesto

La aplicación no se cargará si ha editado manualmente una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación para hacer referencia a una versión anterior de un ensamblado de .NET Framework. Por ejemplo, si agregó una referencia al ensamblado System.Net para una versión de la .NET Framework anterior a la versión especificada en el manifiesto, se produciría un error. En general, no debe intentar especificar referencias a ensamblados de .NET Framework individuales, ya que la versión de la .NET Framework en la que se ejecuta la aplicación se especifica como una dependencia en el manifiesto de aplicación.

## <a name="manifest-parsing-issues"></a>Problemas de análisis de manifiestos

Los archivos de manifiesto utilizados por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] son archivos XML y deben tener el formato correcto y válidos: deben obedecer las reglas de sintaxis XML y usar solo los elementos y atributos definidos en el esquema XML correspondiente.

Algo que puede causar problemas en un archivo de manifiesto es seleccionar un nombre para la aplicación que contenga un carácter especial, como una comilla simple o doble. El nombre de la aplicación forma parte de su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identidad. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Actualmente no analiza las identidades que contienen caracteres especiales. Si no se puede activar la aplicación, asegúrese de que está usando solo caracteres alfabéticos y numéricos para el nombre e intente implementarlo de nuevo.

Si ha editado manualmente los manifiestos de implementación o de aplicación, es posible que los haya dañado involuntariamente. El manifiesto dañado impedirá una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalación correcta. Para depurar estos errores en tiempo de ejecución, haga clic en **detalles** en el cuadro de diálogo **error de ClickOnce** y lea el mensaje de error en el registro. El registro mostrará uno de los siguientes mensajes:

- Una descripción del error de sintaxis, así como el número de línea y la posición del carácter en que se produjo el error.

- Nombre de un elemento o atributo que se usa en infracción del esquema del manifiesto. Si ha agregado XML manualmente a los manifiestos, tendrá que comparar las adiciones a los esquemas de manifiesto. Para obtener más información, vea [manifiesto de implementación ClickOnce](../deployment/clickonce-deployment-manifest.md) y [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).

- Un conflicto de identificador. Las referencias de dependencia en los manifiestos de implementación y de aplicación deben ser únicas en sus `name` `publicKeyToken` atributos y. Si ambos atributos coinciden entre dos elementos de un manifiesto, el análisis del manifiesto no se realizará correctamente.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauciones al cambiar manualmente manifiestos o aplicaciones

Al actualizar un manifiesto de aplicación, debe volver a firmar el manifiesto de aplicación y el manifiesto de implementación. El manifiesto de implementación contiene una referencia al manifiesto de aplicación que incluye el hash de ese archivo y su firma digital.

### <a name="precautions-with-deployment-provider-usage"></a>Precauciones con el uso del proveedor de implementación

El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación tiene una `deploymentProvider` propiedad que señala a la ruta de acceso completa de la ubicación desde la que se debe instalar y atender la aplicación:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Esta ruta de acceso se establece cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea la aplicación y es obligatoria para las aplicaciones instaladas. La ruta de acceso señala a la ubicación estándar donde el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalador instalará la aplicación y buscará actualizaciones. Si usa el comando **xcopy** para copiar una [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación en una ubicación diferente, pero no cambia la `deploymentProvider` propiedad, seguirá haciendo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] referencia a la ubicación original cuando intente descargar la aplicación.

Si desea trasladar o copiar una aplicación, también debe actualizar la ruta de `deploymentProvider` acceso, de modo que el cliente se instale realmente desde la nueva ubicación. La actualización de esta ruta de acceso es principalmente un problema si ha instalado aplicaciones. En el caso de las aplicaciones en línea que siempre se inician a través de la dirección URL original, el valor de `deploymentProvider` es opcional. Si `deploymentProvider` se establece, se respetará; de lo contrario, se usará la dirección URL utilizada para iniciar la aplicación como la dirección URL base para descargar los archivos de aplicación.

> [!NOTE]
> Cada vez que actualice el manifiesto, también debe volver a iniciarla.

## <a name="see-also"></a>Consulte también

[Solucionar problemas de las implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md) 
 [Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md) 
 [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
