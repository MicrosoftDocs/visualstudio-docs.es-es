---
title: Registro de VSPackage ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703920"
---
# <a name="vspackage-registration"></a>Registro de VSPackage
VSPackages debe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] advertir que están instalados y deben cargarse. Este proceso se realiza escribiendo información en el registro. Ese es un trabajo típico de un instalador.

> [!NOTE]
> Es una práctica aceptada durante el desarrollo de VSPackage para usar el autorregistro. Sin [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] embargo, los socios no pueden enviar sus productos utilizando el autorregistro como parte de la configuración.

 Las entradas del Registro en un paquete de Windows Installer generalmente se realizan en la tabla Registro. También puede registrar extensiones de archivo en la tabla Registro. Sin embargo, Windows Installer proporciona compatibilidad integrada a través del identificador de programación (ProgId), las tablas de clase, extensión y verbo. Para obtener más información, vea [Tablas de base de datos](/windows/desktop/Msi/database-tables).

 Asegúrese de que las entradas del registro están asociadas con el componente adecuado para la estrategia en paralelo elegida. Por ejemplo, las entradas del Registro para un archivo compartido deben estar asociadas con el componente de Windows Installer de ese archivo. Del mismo modo, las entradas del registro para un archivo específico de la versión deben estar asociadas con el componente de ese archivo. De lo contrario, instalar o desinstalar el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage para una versión de podría interrumpir el VSPackage en otras versiones. Para obtener más información, vea [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> La forma más fácil de administrar el registro es utilizar los mismos datos en los mismos archivos tanto para el registro de desarrollador como para el registro en tiempo de instalación. Por ejemplo, algunas herramientas de desarrollo del instalador pueden consumir archivos en formato .reg en tiempo de compilación. Si los desarrolladores mantienen archivos .reg para su propio desarrollo y depuración diaria, esos mismos archivos se pueden incluir automáticamente en el instalador. Si no puede compartir automáticamente los datos de registro, debe asegurarse de que la copia de los datos de registro del instalador esté actualizada.

## <a name="registering-unmanaged-vspackages"></a>Registro de VSPackages no administrados
 VSPackages no administrados (incluidos los generados por la plantilla de paquete de Visual Studio) usan archivos .rgs de estilo ATL para almacenar información de registro. El formato de archivo .rgs es específico de ATL y generalmente no se puede consumir tal cual mediante una herramienta de creación de instalación. La información de registro para el instalador de VSPackage debe mantenerse por separado. Por ejemplo, los desarrolladores pueden mantener los archivos en formato .reg sincronizados con los cambios de archivo .rgs. Los archivos .reg se pueden combinar con RegEdit para el trabajo de desarrollo o consumirlos por un instalador.

## <a name="registering-managed-vspackages"></a>Registro de VSPackages administrados
 La herramienta RegPkg lee los atributos de registro de un VSPackage administrado y puede escribir la información directamente en el registro o escribir archivos de formato .reg que puede consumir un instalador.

> [!NOTE]
> La herramienta RegPkg no es redistribuible y no se puede usar para registrar un VSPackage en el sistema de un usuario.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por qué VSPackages no debe registrarse automáticamente en el momento de la instalación
 Los instaladores de VSPackage no deben confiar en el autorregistro. A primera vista, mantener los valores del registro de un VSPackage sólo en el propio VSPackage parece una buena idea. Dado que los desarrolladores necesitan los valores del registro disponibles para su trabajo de rutina y pruebas, tiene sentido evitar mantener una copia independiente de los datos del registro en el instalador. El instalador puede confiar en el propio VSPackage para escribir valores del Registro.

 Si bien es bueno en teoría, el autorregistro tiene varios defectos que lo hacen inadecuado para la instalación de VSPackage:

- La compatibilidad correcta con la instalación, la desinstalación, la reversión de la instalación y la reversión de la desinstalación requiere que cree cuatro acciones personalizadas para cada VSPackage administrado que se autoregistre mediante una llamada a RegPkg.

- El enfoque de la compatibilidad en paralelo puede requerir que cree cuatro acciones personalizadas que invoquen RegSvr32 o RegPkg para cada versión compatible de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Una instalación con módulos autoregistrados no se puede revertir de forma segura porque no hay forma de saber si las claves autoregistradas son utilizadas por otra característica o aplicación.

- Los archivos DLL autoregistrados a veces se vinculan a los archivos DLL auxiliares que no están presentes o son la versión incorrecta. En cambio, Windows Installer puede registrar archivos DLL mediante las tablas del Registro sin dependencia del estado actual del sistema.

- Se puede denegar el acceso al código de autorregistro a los recursos de red, como las bibliotecas de tipos, si un componente se especifica como run-from-source y aparece en la tabla SelfReg. Esto puede provocar un error en la instalación del componente durante una instalación administrativa.

## <a name="see-also"></a>Vea también
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Registro de paquetes administrados](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
