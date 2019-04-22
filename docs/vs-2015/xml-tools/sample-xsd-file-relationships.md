---
title: 'Archivo XSD de muestra: Relaciones | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 60126510-b7dd-4cb4-92d3-9883590b92f2
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3c5a461b2aad51fa4fa2d4ac5cc682ae413b6eb1
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653441"
---
# <a name="sample-xsd-file-relationships"></a>Archivo XSD de muestra: Relaciones
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El archivo XSD siguiente se usa en numerosos ejemplos de la documentación del Diseñador de esquemas XSD. Este archivo es un esquema de pedido de compra con anotaciones y documentación.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
  <xs:element name="pet" type="PetType"/>  
  
  <xs:attributeGroup name="NameAgeAttributes">  
    <xs:attribute name="age" type="xs:integer" use="required"/>  
    <xs:attribute name="name" type="xs:string" use="required"/>  
  </xs:attributeGroup>  
  
  <xs:complexType name="PetType">  
    <xs:attributeGroup ref="NameAgeAttributes"/>  
  </xs:complexType>  
  
  <xs:element name="cat" substitutionGroup="pet">  
    <xs:complexType>  
      <xs:complexContent>  
        <xs:extension base="PetType">  
          <xs:sequence>  
            <xs:element name="weight" type="xs:integer"/>  
            <xs:element name="color" type="xs:string"/>  
            <xs:element name="breed" type="xs:integer"/>  
          </xs:sequence>  
        </xs:extension>  
      </xs:complexContent>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:element name="dog" substitutionGroup="pet">  
    <xs:complexType>  
      <xs:complexContent>  
        <xs:extension base="PetType">  
          <xs:sequence>  
            <xs:element name="weight" type="xs:integer"/>  
            <xs:element name="color" type="xs:string"/>  
            <xs:element name="breed" type="xs:integer"/>  
          </xs:sequence>  
        </xs:extension>  
      </xs:complexContent>  
    </xs:complexType>  
  </xs:element>  
  
</xs:schema>  
```
