---
title: Registro de VSPackage | Microsoft Docs
description: Obtenga información sobre el registro de VSPackage, donde los paquetes indican a Visual Studio que están instalados y deben cargarse escribiendo información en el registro.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 88c8294042bb61939a52f4053f5b27ae915e01df
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487990"
---
# <a name="vspackage-registration"></a>Registro de VSPackage
Los VSPackages deben informar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de que están instalados y deben cargarse. Este proceso se consigue escribiendo información en el registro. Es un trabajo típico de un instalador.

> [!NOTE]
> Se trata de una práctica aceptada durante el desarrollo de VSPackage para usar el registro automático. Sin embargo, los [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] asociados no pueden enviar sus productos mediante el registro automático como parte de la instalación de.

 Las entradas del registro en un paquete de Windows Installer se suelen realizar en la tabla del registro. También puede registrar extensiones de archivo en la tabla del registro. Sin embargo, Windows Installer proporciona compatibilidad integrada a través de las tablas de identificador de programación (ProgId), clase, extensión y verbo. Para obtener más información, vea [tablas de base de datos](/windows/desktop/Msi/database-tables).

 Asegúrese de que las entradas del registro estén asociadas al componente que sea adecuado para la estrategia en paralelo elegida. Por ejemplo, las entradas del registro para un archivo compartido deben estar asociadas al componente de Windows Installer de ese archivo. Del mismo modo, las entradas del registro para un archivo específico de la versión deben estar asociadas al componente de ese archivo. De lo contrario, la instalación o desinstalación del VSPackage para una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podría interrumpir el VSPackage en otras versiones. Para obtener más información, vea [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> La forma más fácil de administrar el registro es usar los mismos datos en los mismos archivos para el registro del desarrollador y el registro en tiempo de instalación. Por ejemplo, algunas herramientas de desarrollo de instalador pueden consumir el archivo en formato. reg en tiempo de compilación. Si los desarrolladores mantienen archivos. reg para su propio desarrollo y depuración cotidianos, esos mismos archivos se pueden incluir automáticamente en el instalador. Si no puede compartir automáticamente los datos de registro, debe asegurarse de que la copia de los datos de registro del instalador es actual.

## <a name="registering-unmanaged-vspackages"></a>Registrar VSPackages no administrados
 Los VSPackages no administrados (incluidos los generados por la plantilla de paquete de Visual Studio) usan archivos. RGS de estilo ATL para almacenar información de registro. El formato de archivo. RGS es específico de ATL y, por lo general, no se puede consumir tal cual mediante una herramienta de creación de instalación. La información de registro para el instalador de VSPackage se debe mantener por separado. Por ejemplo, los desarrolladores pueden mantener los archivos en formato. reg sincronizados con los cambios en el archivo. RGS. Los archivos. reg se pueden combinar con regedit para el trabajo de desarrollo o un instalador.

## <a name="registering-managed-vspackages"></a>Registrar VSPackages administrados
 La herramienta RegPkg Lee los atributos de registro de un VSPackage administrado y puede escribir la información directamente en el registro o escribir archivos. reg-Format que un instalador puede consumir.

> [!NOTE]
> La herramienta RegPkg no es redistribuible y no se puede usar para registrar un VSPackage en el sistema de un usuario.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por qué los paquetes de VSPackages no deben Self-Register en el momento de la instalación
 Los instaladores de VSPackage no deben confiar en el registro automático. A primera vista, mantener los valores del registro de un VSPackage solo en el propio VSPackage parece una buena idea. Dado que los desarrolladores necesitan que los valores del registro estén disponibles para su trabajo rutinario y las pruebas, tiene sentido evitar mantener una copia independiente de los datos del registro en el instalador. El instalador puede confiar en el propio VSPackage para escribir valores del registro.

 Aunque es bueno en teoría, el registro automático tiene varios errores que hacen que no sea adecuado para la instalación de VSPackage:

- La instalación correcta, desinstalación, reversión de la instalación y desinstalación de desinstalación requiere la creación de cuatro acciones personalizadas para cada VSPackage administrado que se registra automáticamente mediante una llamada a RegPkg.

- Su enfoque para la compatibilidad en paralelo puede requerir que cree cuatro acciones personalizadas que invocan a RegSvr32 o RegPkg para cada versión admitida de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Una instalación con módulos autoregistrados no se puede revertir de forma segura porque no hay ninguna manera de indicar si otras características o aplicaciones usan las claves registradas automáticamente.

- A veces, los archivos dll de registro automático se vinculan a archivos dll auxiliares que no están presentes o que son de una versión incorrecta. Por el contrario, Windows Installer pueden registrar archivos DLL mediante las tablas del registro sin depender del estado actual del sistema.

- El código de registro automático puede denegar el acceso a los recursos de red, como las bibliotecas de tipos, si un componente se especifica como Run-from-Source y se muestra en la tabla SelfReg. Esto puede hacer que se produzca un error en la instalación del componente durante una instalación administrativa.

## <a name="see-also"></a>Vea también
- [Windows Installer](/windows/desktop/Msi/windows-installer-portal)
- [Registro de paquetes administrados](/previous-versions/bb166783(v=vs.100))