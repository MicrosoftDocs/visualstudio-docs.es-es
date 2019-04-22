---
title: Procedimiento Crear un documento XML basado en un esquema XSD | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70b42db031c200f16a9189c4d750c9011e739029
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647578"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Procedimiento Crear un documento XML basado en un esquema XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El **generar XML de ejemplo** característica genera un archivo XML de ejemplo basado en el archivo de esquema XML (XSD).  
  
 Puede usar esta opción en los escenarios siguientes:  
  
- Si desea comprender el uso de varias construcciones en un esquema dado.  
  
- Confirmar que el esquema hace aquello que estaba previsto.  
  
  El **generar XML de ejemplo** característica solo está disponible en los elementos globales y requiere un conjunto de esquemas XML válido.  
  
  Esta característica suele generar documentos XML válidos. Sin embargo, si el esquema contiene uno o varios de los siguientes elementos, la muestra podría no ser válida:  
  
- Las restricciones de identidad `xs:key`, `xs:keyref` y `xs:unique`.  
  
- Facetas `xs:pattern`.  
  
- Enumeraciones del tipo `xs:QName`.  
  
- Los tipos `xs:ENTITY`, `xs:ENTITIES` y `xs:NOTATION`.  
  
  Además, observe que el contenido de `xs:base64Binary` solo se generará si aparecen enumeraciones en el esquema para ese tipo.  
  
### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Para generar un documento de instancia XML basado en el archivo XSD  
  
1.  Siga los pasos de [Cómo: Crear y editar un archivo de esquema XSD](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).  
  
2.  En el [Explorador de esquemas XML](../xml-tools/xml-schema-explorer.md), haga clic en el `PurchaseOrder` elemento global. Seleccione **generar XML de ejemplo**.  
  
     Al seleccionar esta opción, se generará el archivo PurchaseOrder.xml con el contenido XML de ejemplo siguiente y se abrirá en el Editor XML:  
  
    ```  
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
 [Trabajo con datos XML](../xml-tools/working-with-xml-data.md)
