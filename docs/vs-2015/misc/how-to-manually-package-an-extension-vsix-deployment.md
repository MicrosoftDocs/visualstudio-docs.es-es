---
title: Filtrar Empaquetar manualmente una extensión (implementación VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: 3537879481430490d32ab30f8f6a2f9f7353659b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995405"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Filtrar Empaquetar manualmente una extensión (implementación VSIX)
Puede crear un paquete VSIX para encapsular una extensión [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para la implementación. Puede crear el paquete de tres formas distintas:  
  
- Crear un proyecto de paquete VSIX mediante una de las plantillas de extensibilidad que se incluyen en el SDK de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Esta es la opción más sencilla para la mayoría de los escenarios.  
  
- Ajustar el resultado de su proyecto de extensión en un [proyecto VSIX](../extensibility/vsix-project-template.md)vacío. Se recomienda esta opción para las plantillas, los ensamblados no compatibles y los tipos personalizados.  
  
- Crear manualmente un paquete VSIX. Se recomienda esta opción solo cuando las otras dos opciones no están disponibles.  
  
  Este documento describe la tercera opción.  
  
## <a name="creating-a-vsix-package"></a>Crear un paquete VSIX  
 Para empaquetar manualmente una extensión, agregue un archivo extension.manifest y un archivo [Content_Types].xml al proyecto de extensión. A continuación, colóquelos en un archivo comprimido junto con el resultado de la compilación y cambie el nombre del archivo comprimido para que tenga una extensión de nombre de archivo .vsix. La extensión que se debe empaquetar debe ser de un tipo compatible con el [esquema VSIX](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Los nombres de archivos en paquetes VSIX no puede contener espacios ni caracteres reservados en identificadores de recursos uniforme (URI), como se definen en [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Para crear manualmente un paquete VSIX  
  
1.  Cree una extensión de Visual Studio de un tipo compatible con el esquema VSIX.  
  
2.  Cree un archivo XML y asígnele el nombre `extension.vsixmanifest`.  
  
3.  Rellene el archivo extension.vsixmanifest según el esquema VSIX. Para obtener un ejemplo de manifiesto, vea [Elemento PackageManifest (elemento Root, esquema VSX)](http://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Cree un segundo archivo XML y asígnele el nombre `[Content_Types].xml`.  
  
5.  Rellene el archivo de [Content_Types] .xml como se especifica en [la estructura de la Content_types\]archivo .xml](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6.  Coloque ambos archivos XML en un directorio junto con la extensión que se va a implementarse.  
  
     En el caso de una plantilla de proyecto o de elemento, coloque el archivo .zip que contiene la plantilla en la misma carpeta que los archivos XML. No coloque los archivos XML en el archivo zip.  
  
     En los demás casos, coloque los archivos XML en el mismo directorio que el del resultado de la compilación.  
  
7.  En el Explorador de Windows, haga clic con el botón secundario en la carpeta que contiene el contenido de la extensión y los dos archivos XML, haga clic en **Enviar a**, y luego en **Carpeta comprimida (zip)**.  
  
8.  Cambie el nombre del archivo .zip resultante a *Nombre de archivo*.vsix, donde *Nombre de archivo* corresponde al nombre del archivo redistribuible que instala el paquete.  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de Visual Studio de trasvase de registros](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomía de un paquete VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Elemento PackageManifest (elemento Root, esquema VSX)](http://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)