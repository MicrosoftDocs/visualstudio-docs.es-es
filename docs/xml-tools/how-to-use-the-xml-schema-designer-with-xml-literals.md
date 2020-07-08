---
title: Procedimiento Usar el Diseñador de esquemas XML con literales XML
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b515092087ab213db5d3002f00c56753c2e3de14
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814647"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedimiento Uso del diseñador de esquemas XML con literales XML

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.

## <a name="create-a-new-visual-basic-project"></a>Creación de un proyecto de Visual Basic

1. Abra Visual Studio.

2. Cree un proyecto de **Aplicación de consola** de Visual Basic denominado **XMLLiterals**.

     El proyecto nuevo contiene un archivo de código fuente de Visual Basic, *Module1.vb*.

## <a name="add-an-existing-xsd-file"></a>Incorporación de un archivo XSD existente

1. Abra un archivo de texto nuevo en el Bloc de notas. Copie el código de ejemplo del Esquema XML del [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.

2. Guarde el archivo en alguna ubicación con el nombre *PurchaseOrderSchema.xsd*.

3. En el **Explorador de soluciones**, haga clic con el botón derecho en el nombre del proyecto, seleccione **Agregar** y, después, seleccione **Elemento existente**. Aparece el cuadro de diálogo **Agregar elemento existente**. Busque el archivo *PurchaseOrderSchema.xsd*, selecciónelo y, a continuación, haga clic en **Agregar**.

     El proyecto XMLLiterals contiene ahora dos archivos: *Module1.vb* y *PurchaseOrderSchema.xsd*.

## <a name="add-code"></a>Incorporación de código

Para agregar el código de Visual Basic con un literal XML, basado en el archivo XSD incluido en el proyecto:

1. Reemplace el código del archivo *Module1.vb* por el código siguiente:

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

2. Haga clic con el botón derecho en cualquier nodo de XML de un literal XML o una importación de espacio de nombres de XML y seleccione **Mostrar en Explorador de esquemas**.

   El **Explorador de esquemas XML** se muestra en paralelo con un archivo Visual Basic que tiene asociado el literal XML con el conjunto de esquemas XML.
