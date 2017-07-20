---
title: "Extensión de Excel de muestra: ExtensionPackage (Clase) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 20e3ac96d5b12002b11a9e93b413c48738f57153
ms.contentlocale: es-es
ms.lasthandoff: 05/19/2017

---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensión de Excel de muestra: ExtensionPackage (Clase)
Esta clase extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> y proporciona el punto de entrada para una prueba de IU codificada que está probando una hoja de cálculo [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="assembly-attribute"></a>Assembly (Atributo)  
 El archivo comienza con un atributo Assembly que identifica el ensamblado como una extensión de prueba de interfaz de usuario.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Este atributo declara el nombre de la clase base, el nombre de la clase de paquete y el nombre de clase completo de la clase de paquete de extensión personalizada.  
  
## <a name="simple-properties"></a>Propiedades simples  
 Esta clase tiene propiedades que proporcionan valores que usa el marco de pruebas de IU codificadas para identificar y describir el ensamblado y la extensión. Para obtener más información, vea los comentarios del código.  
  
## <a name="getservice-method"></a>GetService (Método)  
 El método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> es el único punto de entrada usado por el marco de pruebas de IU codificadas para acceder al administrador de tecnología, el proveedor de propiedades y el filtro de acción, identificado por la clase base para cada objeto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

