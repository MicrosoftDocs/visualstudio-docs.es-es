---
title: 'Cómo: Crear un documento XML basado en un esquema XSD'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d3da2e6b5b0c9ea2701524c0fb2fde1e1313687
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549095"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Cómo: crear un documento XML basado en un esquema XSD

El **generar XML de ejemplo** característica genera un archivo XML de ejemplo basado en el archivo de esquema XML (XSD).

 Puede usar esta opción en los escenarios siguientes:

-   Si desea comprender el uso de varias construcciones en un esquema dado.

-   Confirmar que el esquema hace aquello que estaba previsto.

El **generar XML de ejemplo** característica solo está disponible en los elementos globales y requiere un conjunto de esquemas XML válido.

Esta característica suele generar documentos XML válidos. Sin embargo, si el esquema contiene uno o varios de los siguientes elementos, la muestra podría no ser válida:

-   Las restricciones de identidad `xs:key`, `xs:keyref` y `xs:unique`.

-   Facetas `xs:pattern`.

-   Enumeraciones del tipo `xs:QName`.

-   Los tipos `xs:ENTITY`, `xs:ENTITIES` y `xs:NOTATION`.

Además, observe que el contenido de `xs:base64Binary` solo se generará si aparecen enumeraciones en el esquema para ese tipo.

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Para generar un documento de instancia XML basado en el archivo XSD

1.  Siga los pasos de [Cómo: crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2.  En el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md), haga clic en el `PurchaseOrder` elemento global. Seleccione **generar XML de ejemplo**.

     Al seleccionar esta opción, la PurchaseOrder. *xml* archivo con el siguiente contenido XML de ejemplo se genera y se abre en el Editor de XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>Vea también

- [Trabajar con datos XML](../xml-tools/working-with-xml-data.md)