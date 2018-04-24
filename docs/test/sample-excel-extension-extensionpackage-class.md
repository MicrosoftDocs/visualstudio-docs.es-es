---
title: 'Extensión de Excel de muestra: ExtensionPackage (Clase) | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 623b18a22441fdd2478716582d94a8b878c31d54
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
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

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
