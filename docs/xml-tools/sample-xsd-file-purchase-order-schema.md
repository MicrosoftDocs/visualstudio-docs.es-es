---
title: 'Archivo XSD de ejemplo: esquema de pedido de compra'
description: Vea el archivo XSD de ejemplo de un esquema de pedido de compra que se usa en varios ejemplos de la documentación del Diseñador de esquemas XSD.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: sample
ms.assetid: f92b63b5-ec61-43b5-ae1e-63432a7a7e30
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32140ce05761fa5b8a067dfde04b65efa2a91a66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951646"
---
# <a name="sample-xsd-file-purchase-order-schema"></a>Archivo XSD de muestra: esquema de pedido de compra

El archivo XSD siguiente se usa en numerosos ejemplos de la documentación del Diseñador de esquemas XSD. Este archivo es un esquema de pedido de compra.

```xml
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"
          xmlns:tns="http://tempuri.org/PurchaseOrderSchema.xsd"
          targetNamespace="http://tempuri.org/PurchaseOrderSchema.xsd"
          elementFormDefault="qualified">
  <xsd:element name='comment' type='xsd:string'/>

  <xsd:element name='purchaseOrder' type='tns:PurchaseOrderType'/>

  <xsd:complexType name='USAddress'>
    <xsd:annotation>
      <xsd:documentation>
        Purchase order schema for Example.Microsoft.com.
      </xsd:documentation>
    </xsd:annotation>
    <xsd:sequence>
      <xsd:element name='name'   type='xsd:string'/>
      <xsd:element name='street' type='xsd:string'/>
      <xsd:element name='city'   type='xsd:string'/>
      <xsd:element name='state'  type='xsd:string'/>
      <xsd:element name='zip'    type='xsd:decimal'/>
    </xsd:sequence>
    <xsd:attribute name='country' type='xsd:NMTOKEN' fixed='US'/>
  </xsd:complexType>

  <xsd:simpleType name='SKU'>
    <xsd:restriction base='xsd:string'>
      <xsd:pattern value='\d{3}\w{3}'/>
    </xsd:restriction>
  </xsd:simpleType>

  <xsd:complexType name='Items'>
    <xsd:sequence>
      <xsd:element name='item' minOccurs='0' maxOccurs='unbounded'>
        <xsd:complexType>
          <xsd:sequence>
            <xsd:element name='productName' type='xsd:string'/>
            <xsd:element name='quantity'>
              <xsd:simpleType>
                <xsd:restriction base='xsd:positiveInteger'>
                  <xsd:minInclusive value='1'/>
                  <xsd:maxExclusive value='100'/>
                </xsd:restriction>
              </xsd:simpleType>
            </xsd:element>
            <xsd:element name='USPrice'  type='xsd:decimal'/>
            <xsd:element ref='tns:comment'/>
            <xsd:element name='shipDate' type='xsd:date' minOccurs='0'/>
          </xsd:sequence>
          <xsd:attribute name='partNum' type='tns:SKU'/>
        </xsd:complexType>
      </xsd:element>
    </xsd:sequence>
  </xsd:complexType>

  <xsd:complexType name='PurchaseOrderType'>
    <xsd:sequence>
      <xsd:element name='shipTo' type='tns:USAddress'/>
      <xsd:element name='billTo' type='tns:USAddress'/>
      <xsd:element ref='tns:comment' minOccurs='0'/>
      <xsd:element name='items'  type='tns:Items'/>
    </xsd:sequence>
    <xsd:attribute name='orderDate' type='xsd:date'/>
    <xsd:attribute name='confirmDate' type='xsd:date' use='required'/>
  </xsd:complexType>
</xsd:schema>
```

> [!NOTE]
> Las compañías, organizaciones, productos, nombres de dominio, direcciones de correo electrónico, logotipos, personas, lugares y eventos que se citan a modo de ejemplo son ficticios. No se pretende establecer ni se debe inferir ninguna asociación con ninguna empresa, organización, producto, nombre de dominio, dirección de correo electrónico, logotipo, persona, lugar ni evento real.
