---
title: 'Extensión de Excel de muestra: ExtensionPackage (Clase) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672207"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Extensión de Excel de muestra: ExtensionPackage (Clase)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [extender las pruebas de IU codificadas y las grabaciones de acciones para admitir Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
