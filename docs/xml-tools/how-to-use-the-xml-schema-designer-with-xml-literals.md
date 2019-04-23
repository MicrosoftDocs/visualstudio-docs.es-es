---
title: Procedimiento Usar el Diseñador de esquemas XML con literales XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9e92cbdca3ac2c5c366ec054ba79f2e7324986c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067617"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedimiento Uso del diseñador de esquemas XML con literales XML

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Crear un nuevo proyecto de Visual Basic

1. Abra Visual Studio.

2. Crear un nuevo Visual Basic **aplicación de consola** proyecto denominado **XMLLiterals**.

     El nuevo proyecto contiene un archivo de código fuente de Visual Basic, *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Agregar un archivo XSD existente

1. Abra un nuevo archivo de texto en el Bloc de notas. Copie el código de ejemplo de esquema XML de [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.

2. Guarde el archivo en alguna ubicación con el nombre *PurchaseOrderSchema.xsd*.

3. En **el Explorador de soluciones**, haga clic en el nombre del proyecto, seleccione **agregar**y, a continuación, seleccione **elemento existente**. El **Agregar elemento existente** aparece el cuadro de diálogo. Vaya a la *PurchaseOrderSchema.xsd* de archivo, selecciónelo y, a continuación, haga clic en **agregar**.

     El proyecto XMLLiterals ahora contiene dos archivos: *Module1.vb* y *PurchaseOrderSchema.xsd*.

## <a name="add-code"></a>Agregar código

Para agregar código de Visual Basic con un literal XML, según el archivo XSD incluido en el proyecto:

1. Reemplace el código de *Module1.vb* archivo con el código siguiente:

   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

   Module Module1
      Sub Main()

          Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                               <ns:ShipTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:ShipTo>
                               <ns:BillTo country="US">
                                   <ns:name>name1</ns:name>
                                   <ns:street>street1</ns:street>
                                   <ns:city>city1</ns:city>
                                   <ns:state>state1</ns:state>
                                   <ns:zip>1</ns:zip>
                               </ns:BillTo>
                           </ns:PurchaseOrder>

      End Sub
   End Module
   ```

2. Haga clic en cualquier nodo XML en un literal XML o una importación de espacio de nombres XML y seleccione **mostrar en el Explorador de esquema**.

   El **Explorador de esquemas XML** se muestra en paralelo con un archivo de Visual Basic que tiene el literal XML asociado con el conjunto de esquemas XML.