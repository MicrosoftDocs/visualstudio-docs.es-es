---
title: "Registro de VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "registro, VSPackages"
  - "VSPackages, registrar"
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Registro de VSPackage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Debe aconsejar VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que están instalados y que debe cargarse. Este proceso se logra escribiendo información en el registro. Es un trabajo típico de un instalador.  
  
> [!NOTE]
>  Es una práctica aceptada durante el desarrollo de VSPackage para utilizar el registro automático. Sin embargo, [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] asociados no pueden distribuir sus productos con el registro automático como parte del programa de instalación.  
  
 Entradas del registro en un paquete de Windows Installer se realizan normalmente en la tabla del registro. También puede registrar extensiones de archivo en la tabla del registro. Sin embargo, Windows Installer proporciona compatibilidad integrada a través del identificador de programación \(ProgId\), clase, extensión y tablas de verbo. Para obtener más información, consulte [tablas de base de datos](http://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Asegúrese de que las entradas del registro están asociadas con el componente que sea adecuado para su estrategia de side\-by\-side elegido. Por ejemplo, entradas del registro de un archivo compartido deben asociarse con el componente de Windows Installer de ese archivo. Del mismo modo, las entradas del registro para un archivo específico de la versión se deben asociadas con el componente de ese archivo. De lo contrario, instalar o desinstalar el VSPackage para una versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podría interrumpir el VSPackage en otras versiones. Para obtener más información, vea [Compatibilidad con varias versiones de Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
>  Administrar registro de la manera más fácil es usar los mismos datos en los mismos archivos de registro del programador y el registro durante la instalación. Por ejemplo, algunas herramientas de desarrollo de instalador pueden consumir el archivo con formato .reg en tiempo de compilación. Si los programadores mantienen archivos .reg para su propio desarrollo día a día y depuración, esos mismos archivos pueden incluirse en el programa de instalación automáticamente. Si no se comparte automáticamente datos de registro, debe asegurarse de que la copia del instalador de los datos de registro es actual.  
  
## Registrar VSPackages administrado  
 VSPackages administrados \(incluidos los generados por la plantilla de paquete de Visual Studio\) utilice archivos de estilo ATL .rgs para almacenar la información de registro. El formato de archivo .rgs es específico de ATL y generalmente no puede utilizarse como\-es una herramienta de creación de instalación. Información de registro para el instalador de VSPackage debe mantenerse por separado. Por ejemplo, los desarrolladores pueden mantener los archivos en formato .reg sincronizados con .rgs cambios en el archivo. Los archivos .reg pueden ser combinados con RegEdit para el trabajo de desarrollo o consume un instalador.  
  
## Registrar VSPackages administrado  
 La herramienta RegPkg lee los atributos del registro de un VSPackage administrado y puede escribir la información directamente en el registro o escribir archivos de formato .reg que pueden utilizarse en un instalador.  
  
> [!NOTE]
>  La herramienta RegPkg no es redistribuible y no se puede usar para registrar un VSPackage en el sistema del usuario.  
  
## ¿Por qué VSPackages no debe registrarse automáticamente durante la instalación  
 Los instaladores de VSPackage no deben confiar en el registro automático. A primera vista, el mantenimiento de los valores del registro de un VSPackage sólo en el VSPackage del propio parece una buena idea. Dado que los desarrolladores tienen los valores de registro disponibles para su trabajo rutinario y pruebas, conviene evitar mantener una copia independiente de los datos del registro en el programa de instalación. El instalador puede basarse en el paquete VSPackage, para escribir valores del registro.  
  
 Mientras bueno en teoría, registro automático tiene varios errores que inapropiada para la instalación de VSPackage:  
  
-   Admitir correctamente la instalación, desinstalación, revertir la instalación y reversión de desinstalación requiere crear cuatro acciones personalizadas para cada paquete VSPackage administrado que se registra mediante una llamada a RegPkg.  
  
-   El enfoque a la compatibilidad en paralelo puede requerir que lo cree cuatro acciones personalizadas que invocación RegSvr32 o RegPkg para todas las versiones compatibles de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   No se puede revertir una instalación con módulos registrados automáticamente sin ningún riesgo porque no hay ninguna manera de indicarle si se usan las claves automáticamente registradas por otra aplicación o característica.  
  
-   DLLs registradas automáticamente a veces vinculan a DLL auxiliar que no están presentes o tienen una versión incorrecta. En cambio, Windows Installer puede registrar archivos DLL mediante las tablas de registro con ninguna dependencia en el estado actual del sistema.  
  
-   Código de registro automático se puede denegar acceso a recursos de red, como bibliotecas de tipos, si es un componente tanto especificado como ejecutar desde el origen y se muestra en la tabla SelfReg. Esto puede provocar que la instalación del componente a un error durante una instalación administrativa.  
  
## Vea también  
 [Windows Installer](http://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Managed Package Registration](http://msdn.microsoft.com/es-es/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)