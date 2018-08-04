---
title: Registro de VSPackage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 29592f7956177a4894967d7f393605a54f7ec07b
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513166"
---
# <a name="vspackage-registration"></a>Registro de VSPackage
Debe aconsejar VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que están instaladas y deben cargarse. Este proceso se consigue mediante la escritura de información en el registro. Es un trabajo típico de un instalador.  
  
> [!NOTE]
>  Es una práctica aceptada durante el desarrollo de VSPackage para usar el registro automático. Sin embargo, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] asociados no pueden distribuir sus productos mediante el registro de autoservicio como parte del programa de instalación.  
  
 Las entradas del registro en un paquete de Windows Installer se realizan normalmente en la tabla del registro. También puede registrar las extensiones de archivo en la tabla del registro. Sin embargo, Windows Installer proporciona compatibilidad integrada a través del identificador de programación (ProgId), clase, extensión y las tablas de verbo. Para obtener más información, consulte [tablas de base de datos](/windows/desktop/Msi/database-tables).  
  
 Asegúrese de que las entradas del registro están asociadas con el componente que es adecuado para su estrategia de side-by-side elegido. Por ejemplo, las entradas del registro de un archivo compartido deben asociarse con el componente de Windows Installer de ese archivo. Del mismo modo, las entradas del registro para un archivo específico de la versión se deben asociadas con el componente de ese archivo. En caso contrario, instalar o desinstalar el paquete de VS para una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podría interrumpir el paquete de VS en otras versiones. Para obtener más información, consulte [que admiten varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  La manera más fácil de administrar el registro es usar los mismos datos en los mismos archivos de registro de desarrollador y registro durante la instalación. Por ejemplo, algunas herramientas de desarrollo de instalador pueden consumir el archivo .reg formato en tiempo de compilación. Si los desarrolladores mantienen archivos .reg para su propio diario desarrollo y depuración, esos mismos archivos se pueden incluir en el programa de instalación automáticamente. Si no se puede compartir automáticamente los datos de registro, debe asegurarse de que la copia del instalador de los datos de registro es actual.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrar los VSPackages no administrados  
 Los VSPackages no administrados (incluidos los generados por la plantilla de paquete de Visual Studio) usar archivos .rgs de estilo ATL para almacenar información de registro. El formato de archivo .rgs es específico de ATL y generalmente no se pueden consumir como-es mediante una instalación de herramienta de creación. Información de registro para el instalador de paquete VSPackage debe mantenerse por separado. Por ejemplo, los desarrolladores pueden mantenerse los archivos con formato .reg en sincronización con .rgs cambios en el archivo. Los archivos .reg pueden se combinan con RegEdit para trabajos de desarrollo o utilizados por un instalador.  
  
## <a name="registering-managed-vspackages"></a>Registro de VSPackages administrados  
 La herramienta RegPkg lee los atributos de registro de un VSPackage administrado y puede escribir la información directamente al registro o escribir archivos de formato .reg que pueden utilizarse en un instalador.  
  
> [!NOTE]
>  La herramienta RegPkg no es redistribuible y no se puede usar para registrar un VSPackage en el sistema del usuario.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>¿Por qué los VSPackages no deben registrarse automáticamente en tiempo de instalación  
 Los instaladores de VSPackage no deben confiar en el registro automático. A primera vista, mantener los valores del registro de un VSPackage solo en el VSPackage del propio parece una buena idea. Dado que los desarrolladores necesitan los valores del registro disponibles para su trabajo rutinario y las pruebas, tiene sentido para evitar el mantenimiento de una copia independiente de los datos del registro en el instalador. El instalador puede basarse en el VSPackage para escribir los valores del registro.  
  
 Además de bueno en teoría, autorregistro tiene varios defectos que hacen que no son adecuados para la instalación de VSPackage:  
  
-   Admitir correctamente la instalación, desinstalación, reversión de la instalación y desinstalación rollback, deberá crear cuatro acciones personalizadas para cada VSPackage administrado que se registra automáticamente mediante una llamada a RegPkg.  
  
-   El enfoque para la compatibilidad en paralelo puede requerir que crear cuatro acciones personalizadas que invocan RegSvr32 o RegPkg para todas las versiones compatibles de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   Una instalación con módulos registrados automáticamente no se puede revertir sin ningún riesgo porque no hay ninguna manera de indicar si se utilizan las claves autorregistrar por otra aplicación o característica.  
  
-   DLL autorregistrar a veces se vinculan a archivos DLL auxiliar que no están presentes o tienen una versión incorrecta. En cambio, Windows Installer puede registrar la DLL mediante las tablas de registro sin ninguna dependencia con el estado actual del sistema.  
  
-   Código de registro automático se puede denegar el acceso a recursos de red, como bibliotecas de tipos, si es un componente especificado como la ejecución desde origen tanto se muestra en la tabla SelfReg. Esto puede causar la instalación del componente a un error durante una instalación administrativa.  
  
## <a name="see-also"></a>Vea también  
 [Windows Installer](/windows/desktop/Msi/windows-installer-portal)   
 [Registro de paquetes administrados](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)