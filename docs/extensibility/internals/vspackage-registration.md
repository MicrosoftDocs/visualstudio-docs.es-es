---
title: Registro de VSPackage | Documentos de Microsoft
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
ms.openlocfilehash: 348010982b015eaf19ba4de559eca66bb24930a3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="vspackage-registration"></a>Registro de VSPackage
Debe aconsejar VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que están instalados y que debe cargarse. Este proceso se consigue mediante la escritura de información en el registro. Es un trabajo típico de un instalador.  
  
> [!NOTE]
>  Es una práctica aceptada durante el desarrollo de VSPackage para usar el registro automático. Sin embargo, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] asociados no pueden distribuir sus productos con el registro automático como parte del programa de instalación.  
  
 Entradas del registro en un paquete de Windows Installer se realizan normalmente en la tabla del registro. También puede registrar las extensiones de archivo en la tabla del registro. Sin embargo, Windows Installer proporciona compatibilidad integrada mediante el identificador de programación (ProgId), la clase, la extensión y la tablas de verbo. Para obtener más información, consulte [tablas de base de datos](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Asegúrese de que las entradas del registro están asociadas con el componente que es adecuado para su estrategia de side-by-side elegida. Por ejemplo, las entradas del registro de un archivo compartido deben asociarse con el componente de Windows Installer de dicho archivo. Del mismo modo, las entradas del registro para un archivo específico de la versión deben asociarse con el componente de ese archivo. En caso contrario, instalar o desinstalar el paquete de VS para una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podría afectar el VSPackage en otras versiones. Para obtener más información, vea [compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  La manera más fácil de administrar el registro es usar los mismos datos en los mismos archivos de registro de desarrollador y registro de hora de la instalación. Por ejemplo, algunas herramientas de desarrollo de instalador pueden consumir el archivo en formato .reg en tiempo de compilación. Si los programadores mantienen archivos .reg para su propio desarrollo diaria y depuración, esos mismos archivos pueden incluirse en el programa de instalación automáticamente. Si no se comparte automáticamente datos de registro, debe asegurarse de que la copia del instalador de los datos de registro es actual.  
  
## <a name="registering-unmanaged-vspackages"></a>Registro de VSPackages no administrados  
 Los VSPackages no administrados (incluidos los generados por la plantilla de paquete de Visual Studio) utilice archivos de .rgs de estilo de ATL para almacenar información de registro. El formato de archivo .rgs es específico de ATL y por lo general no puede utilizarse como-es una herramienta de creación de instalación. Información de registro para el instalador de VSPackage debe mantenerse por separado. Por ejemplo, los desarrolladores pueden mantener los archivos en formato .reg sincronizados con .rgs cambios del archivo. Los archivos .reg pueden ser combinados con RegEdit para trabajos de desarrollo o utilizados por un instalador.  
  
## <a name="registering-managed-vspackages"></a>Registro de VSPackages administrado  
 La herramienta RegPkg lee los atributos de registro de un VSPackage administrado y puede escribir la información directamente en el registro o escribir archivos de formato .reg que se pueden usar en un instalador.  
  
> [!NOTE]
>  La herramienta RegPkg no es redistribuible y no se puede usar para registrar un VSPackage en el sistema del usuario.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>¿Por qué VSPackages no debe registrar automáticamente durante la instalación  
 Los instaladores de VSPackage no deben confiar en el registro automático. A primera vista, conservando los valores de registro de un paquete VSPackage solo en el VSPackage propio parece ser una buena idea. Dado que los desarrolladores tienen los valores de registro disponibles para su trabajo rutinaria y pruebas, conviene evitar mantener una copia independiente de los datos del registro en el programa de instalación. El programa de instalación puede basarse en el VSPackage para escribir valores del registro.  
  
 Además de buena en teoría, el registro automático tiene varios errores que hacen que sea apropiada para la instalación del paquete de VS:  
  
-   Admitir correctamente la instalación, desinstalación, revertir la instalación y desinstalación rollback requiere crear cuatro acciones personalizadas para cada VSPackage administrado que se registra automáticamente mediante una llamada a RegPkg.  
  
-   El enfoque al soporte técnico en paralelo puede requerir que lo cree cuatro acciones personalizadas que invocan RegSvr32 o RegPkg para todas las versiones compatibles de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   No se puede revertir una instalación con módulos registrados automáticamente sin ningún riesgo porque no hay ninguna manera de indicar si se usan las claves automáticamente registradas por otra característica o la aplicación.  
  
-   DLL registradas automáticamente a veces se vinculan a archivos DLL auxiliares no están presente o si tienen una versión incorrecta. En cambio, Windows Installer puede registrar la DLL con las tablas de registro ninguna dependencia en el estado actual del sistema.  
  
-   Código de registro automático puede denegar el acceso a recursos de red, como las bibliotecas de tipos, si es un componente tanto especificado como la ejecución de origen y se muestra en la tabla SelfReg. Esto puede causar la instalación del componente a un error durante una instalación administrativa.  
  
## <a name="see-also"></a>Vea también  
 [Instalador de Windows](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registro de paquetes administrados](http://msdn.microsoft.com/en-us/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)