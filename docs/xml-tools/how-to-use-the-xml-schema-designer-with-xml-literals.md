---
title: 'Cómo: Usar el Diseñador de esquemas XML con literales XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6dd0f709e53a3595437bc432a1d1db9a4d6d5c79
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39379519"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Cómo: usar el Diseñador de esquemas XML con literales XML

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.

## <a name="to-create-a-new-visual-basic-console-application-project"></a>Para crear un proyecto para una aplicación de consola de Visual Basic

1.  Inicie Visual Studio.

2.  Desde el **archivo** menú, seleccione **New**y, a continuación, seleccione **proyecto**. Aparecerá el cuadro de diálogo **Nuevo proyecto** . Para **tipos de proyecto**, seleccione **otros lenguajes,** y, a continuación, seleccione **Visual Basic**. Para **plantillas**, seleccione la aplicación de consola. A continuación, escriba `XMLLiterals` en el **nombre** campo y una ubicación de proyecto en el **ubicación** campo. Haga clic en **Aceptar**.

     Se crea el proyecto. El proyecto XMLLiterals contiene un archivo de código fuente de Visual Basic, *Module1.vb*.

## <a name="to-add-an-existing-xsd-file-to-the-project"></a>Para agregar un archivo XSD existente al proyecto

1.  Abra un nuevo archivo de texto en el Bloc de notas. Copie el código de ejemplo de esquema XML de [esquema de pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.

2.  Guarde el archivo en alguna ubicación con el nombre *PurchaseOrderSchema.xsd*.

3.  En **el Explorador de soluciones**, haga clic en el nombre del proyecto, seleccione **agregar**y, a continuación, seleccione **elemento existente**. El **Agregar elemento existente** aparece el cuadro de diálogo. Vaya a la *PurchaseOrderSchema.xsd* de archivo, selecciónelo y, a continuación, haga clic en **agregar**.

     El proyecto XMLLiterals ahora contiene dos archivos: *Module1.vb* y *PurchaseOrderSchema.xsd*.

## <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Para agregar el código de Visual Basic con un literal XML, basado en el archivo XSD incluido en el proyecto

1.  Reemplace el código de *Module1.vb* archivo con el código siguiente:

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

2.  Haga clic en cualquier nodo XML en un literal XML o una importación de espacio de nombres XML y seleccione **mostrar en el Explorador de esquema**.

     El **Explorador de esquemas XML** se muestra en paralelo con un archivo de Visual Basic que tiene el literal XML asociado con el conjunto de esquemas XML.