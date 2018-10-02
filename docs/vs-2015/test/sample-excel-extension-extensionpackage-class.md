---
title: 'Extensión de Excel de muestra: ExtensionPackage (Clase) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fadfbf9291daf35cea4e7ef3005cf3791c2fe052
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565996"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensión de Excel de muestra: ExtensionPackage (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [extensión de Excel de muestra: ExtensionPackage (clase)](https://docs.microsoft.com/visualstudio/test/sample-excel-extension-extensionpackage-class).  
  
Esta clase extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> y proporciona el punto de entrada para una prueba de IU codificada que está probando una hoja de cálculo [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
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



