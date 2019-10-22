---
title: 'Cómo: usar el diseñador de esquemas XML con literales XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656292"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Cómo: Usar el Diseñador de esquemas XML con literales XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este tema se explica cómo ver un esquema asociado a un literal XML en un proyecto Visual Basic.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>Para crear un proyecto para una aplicación de consola de Visual Basic

1. Inicie Visual Studio 2010.

2. En el menú **archivo** , seleccione **nuevo**y seleccione **proyecto**. Aparecerá el cuadro de diálogo **Nuevo proyecto** . En **tipos de proyecto**, seleccione **otros idiomas** y, a continuación, seleccione **Visual Basic**. En el caso de **las plantillas**, seleccione aplicación de consola. A continuación, escriba `XMLLiterals` en el campo **nombre** y una ubicación del proyecto en el campo **Ubicación** . Haga clic en **Aceptar**.

     Se crea el proyecto. El proyecto XMLLiterals contiene un archivo de código fuente de Visual Basic, Module1.vb.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Para agregar un archivo XSD existente al proyecto

1. Abra un nuevo archivo de texto en el Bloc de notas. Copie el código de ejemplo del esquema XML del [esquema del pedido de compra](../xml-tools/sample-xsd-file-simple-schema.md) y péguelo en el archivo.

2. Guarde el archivo con el nombre PurchaseOrderSchema.xsd.

3. En el Explorador de soluciones, haga clic con el botón derecho en el nombre del proyecto, seleccione **Agregar**y, a continuación, seleccione **elemento existente.** . Aparece el cuadro de diálogo **elemento agregar** . Busque el archivo PurchaseOrderSchema. xsd, selecciónelo y, a continuación, haga clic en **Agregar**.

     El proyecto XMLLiterals ahora contiene dos archivos: Module1.vb y PurchaseOrderSchema.xsd.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Para agregar el código de Visual Basic con un literal XML, basado en el archivo XSD incluido en el proyecto

1. Reemplace el código del archivo Module1.vb por el código siguiente:

    ```
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

2. Haga clic con el botón secundario en cualquier nodo XML de un literal XML o una importación de espacio de nombres XML y seleccione **Mostrar en el explorador de esquemas**.

     El Explorador de esquema XML se muestra en paralelo con un archivo Visual Basic que tiene asociado el literal XML con el conjunto de esquemas XML.
