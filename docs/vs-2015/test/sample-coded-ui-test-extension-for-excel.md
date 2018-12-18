---
title: Extensión de muestra para probar la IU codificada para Excel | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5ccc315b62ffa2e7c70f992a560e55c80eb86dc8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306623"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Extensión de muestra para probar la IU codificada para Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El componente de extensión de la muestra se ejecuta en el proceso de prueba de IU codificada [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y es algo jerárquico con la clase `ExtensionPackage` en la base. Las clases `TechnologyManager`, `ActionFilter` y `PropertyProvider` están en el siguiente nivel, con los elementos de control en el nivel superior.  
  
 ![Arquitectura de extensión de pruebas para Excel](../test/media/excel-extarch.png "Excel_ExtArch")  
Arquitectura de extensión para Excel  
  
## <a name="extension-points"></a>Puntos de extensión  
 Estas clases representan los puntos de extensión que se implementan en el ejemplo para habilitar la prueba de IU codificada para [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Heredada de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, este es el punto de entrada para la extensión de prueba de IU codificada. Implementar esta clase abstracta proporciona al marco de prueba de IU codificada acceso interno al administrador de tecnología de prueba de interfaz de usuario personalizado, al proveedor de propiedades de prueba de IU y al filtro de acción de prueba de IU para probar la nueva interfaz de usuario de prueba de IU codificada. Para obtener más información, consulte [ExtensionPackage (Clase)](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Heredada de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, esta clase proporciona un administrador de tecnología para la grabación de pruebas y reproducción. Para obtener más información, consulte [TechnologyManager (Clase)](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Heredada de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, esta clase proporciona una clase base para la agregación de resultados de la acción de prueba similares en un resultado de prueba única. Para obtener más información, consulte [ActionFilter (Clase)](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Elementos de la tecnología  
 Una clase base heredada de la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>, proporciona la base para los elementos de la tecnología de las pruebas de IU que se pueden grabar y reproducir. Para obtener más información, consulte [Element (Clases)](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Heredada de la clase <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, proporciona una clase base para la compatibilidad con las propiedades de elementos de interfaz de usuario para la reproducción y grabación de pruebas. Para obtener más información, consulte [PropertyProvider (Clase)](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage (Clase)](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager (Clase)](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter (Clase)](../test/sample-excel-extension-actionfilter-class.md)   
 [Element (Clases)](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider (Clase)](../test/sample-excel-extension-propertyprovider-class.md)



