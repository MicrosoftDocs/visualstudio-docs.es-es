---
title: Seguridad y control de versiones, manifiestos problemas en implementaciones ClickOnce | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
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
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ec828d555748dbd31a7746d18170d733d4668c9a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Problemas de seguridad, versiones y manifiestos en implementaciones de ClickOnce

Hay una gran variedad de problemas con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] seguridad, versiones de las aplicaciones y manifiesto de sintaxis y semántica que puede causar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación no se realice correctamente.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce y Control de cuentas de usuario de Windows Vista

En [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], aplicaciones de forma predeterminada se ejecutan como un usuario estándar, incluso si el usuario actual ha iniciado sesión con una cuenta que tenga permisos de administrador. Si una aplicación debe llevar a cabo una acción que requiere permisos de administrador, se indica al sistema operativo, que, a continuación, pide al usuario que escriba sus credenciales de administrador. Esta característica, que se denomina Control de cuentas de usuario (UAC), evita que las aplicaciones realicen modificaciones que pueden afectar a todo el sistema operativo sin la aprobación explícita de un usuario. Las aplicaciones Windows declaran que requieren esta elevación de permisos especificando el `requestedExecutionLevel` atributo en la `trustInfo` sección de su manifiesto de aplicación.

Debido al riesgo de exposición de las aplicaciones a ataques de elevación de seguridad, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicaciones no pueden solicitar la elevación de permisos si UAC está habilitado para el cliente. Cualquier [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación que intenta establecer su `requestedExecutionLevel` atribuir a `requireAdministrator` o `highestAvailable` no se instalará en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

En algunos casos, la [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación podría intentar ejecutar con permisos de administrador debido a la lógica de detección del instalador en [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. En este caso, puede establecer la `requestedExecutionLevel` atributo en el manifiesto de aplicación para `asInvoker`. Esto hará que la propia aplicación para que se ejecute sin la elevación. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Este atributo se agrega automáticamente a todos los manifiestos de aplicación.

Si está desarrollando una aplicación que requiere permisos de administrador para toda la duración de la aplicación, considere la posibilidad de implementar la aplicación mediante la tecnología de Windows Installer (MSI) en su lugar. Para obtener más información, consulte [Fundamentos de Windows Installer](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Aplicaciones de confianza parcial y las cuotas de la aplicación en línea

Si su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación se ejecuta en línea en lugar de a través de una instalación, deben ajustarse a la cuota que se reservan para las aplicaciones en línea. Además, una aplicación de red que se ejecuta en confianza parcial, como con un conjunto restringido de permisos de seguridad, no puede ser mayor que la mitad del tamaño de cuota.

Para obtener más información e instrucciones sobre cómo cambiar la cuota de aplicación en línea, consulte [información general sobre la memoria caché de ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problemas de control de versiones

Puede experimentar problemas si asigna nombres seguros al ensamblado y aumentar el número de versión de ensamblado para reflejar una actualización de la aplicación. Cualquier ensamblado compilado con una referencia a un ensamblado con nombre seguro debe compilarse por sí o el ensamblado intentará hacer referencia a la versión anterior. El ensamblado intentará esto porque el ensamblado está usando el valor de la versión anterior en su solicitud de enlace.

Por ejemplo, supongamos que tiene un ensamblado con nombre seguro en su propio proyecto con la versión 1.0.0.0. Después de compilar el ensamblado, agréguela como una referencia al proyecto que contiene la aplicación principal. Si actualiza el ensamblado, incrementa la versión a 1.0.0.1 e intenta implementar sin volver a compilar también la aplicación, la aplicación no pueda cargar el ensamblado en tiempo de ejecución.

Este error puede ocurrir solamente si está editando el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiestos manualmente; no debería experimentar este error si se genera la implementación mediante Visual Studio.

## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Especificar los ensamblados de individuales de .NET Framework en el manifiesto

La aplicación no se cargará si ha editado manualmente un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implementación para hacer referencia a una versión anterior de un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ensamblado. Por ejemplo, si ha agregado una referencia al ensamblado System.Net para una versión de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] antes de la versión especificada en el manifiesto, a continuación, se producirá un error. En general, no debería intentar especificar referencias a persona [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ensamblados, como la versión de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] en que se ejecuta la aplicación se especifica como una dependencia en el manifiesto de aplicación.

## <a name="manifest-parsing-issues"></a>Análisis de problemas de manifiesto

Los archivos de manifiesto que se usan por [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] son archivos XML, y deben ser correcto y válido: deben cumplir las reglas de sintaxis XML y solo utilizan elementos y atributos definidos en el esquema XML correspondiente.

Algo que puede causar problemas en un archivo de manifiesto consiste en seleccionar un nombre para la aplicación que contiene un carácter especial, como un signo de comillas simples o doble. Nombre de la aplicación forma parte de su [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] identidad. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] actualmente no analiza las identidades que contienen caracteres especiales. Si no se puede activar la aplicación, asegúrese de que se utilizan caracteres alfabéticos y numéricos solo para el nombre e intente implementar de nuevo.

Si ha editado manualmente los manifiestos de implementación o de aplicación, puede haberlos dañado involuntariamente. Un manifiesto dañado evitará una correcta [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalación. Puede depurar estos errores en tiempo de ejecución haciendo clic en **detalles** en el **ClickOnce Error** cuadro de diálogo y leer el mensaje de error en el registro. El registro mostrará uno de los mensajes siguientes:

- Una descripción del error de sintaxis y el número de línea y el carácter posición donde se produjo el error.

- El nombre de un elemento o atributo utilizado infringe el esquema del manifiesto. Si ha agregado manualmente XML a los manifiestos, tendrá que comparar las adiciones a los esquemas del manifiesto. Para obtener más información, consulte [manifiesto de implementación de ClickOnce](../deployment/clickonce-deployment-manifest.md) y [manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).

- Un conflicto de identificador. Las referencias de dependencias en los manifiestos de aplicación e implementación deben ser únicas en ambos sus `name` y `publicKeyToken` atributos. Si ambos atributos coinciden entre dos elementos cualesquiera de un manifiesto, análisis del manifiesto no se realizará correctamente.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Precauciones cuando se cambian manualmente manifiestos o aplicaciones

Cuando se actualiza un manifiesto de aplicación, debe volver a firmar el manifiesto de aplicación y el manifiesto de implementación. El manifiesto de implementación contiene una referencia al manifiesto de aplicación que incluye el hash del archivo y su firma digital.

### <a name="precautions-with-deployment-provider-usage"></a>Precauciones con el uso del proveedor de implementación

El [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifiesto de implementación tiene un `deploymentProvider` propiedad que señala a la ruta de acceso completa de la ubicación desde donde la aplicación debe instalarse y realizando tareas de mantenimiento:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Esta ruta de acceso se establece cuando [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] crea la aplicación y es obligatoria para las aplicaciones instaladas. La ruta apunta a la ubicación estándar donde el [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installer instalará la aplicación de y buscar actualizaciones. Si usas el **xcopy** comando para copiar un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicación a una ubicación diferente, pero no cambie el `deploymentProvider` propiedad, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] todavía hará referencia a la ubicación original cuando intente descargar la aplicación.

Si desea mover o copiar una aplicación, también debe actualizar el `deploymentProvider` ruta de acceso, por lo que el cliente se instala realmente desde la nueva ubicación. La actualización de esta ruta de acceso es principalmente un problema si ha instalado las aplicaciones. Para las aplicaciones en línea que siempre se inician a través de la dirección URL original, establecer el `deploymentProvider` es opcional. Si `deploymentProvider` está establecido, se respetará; en caso contrario, se utilizará la dirección URL utilizada para iniciar la aplicación como la dirección URL base para descargar los archivos de la aplicación.

> [!NOTE]
> Cada vez que actualice el manifiesto debe también firmarlo de nuevo.

## <a name="see-also"></a>Vea también

[Solucionar problemas en implementaciones ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Proteger las aplicaciones ClickOnce](../deployment/securing-clickonce-applications.md)  
[Elegir una estrategia de implementación ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)