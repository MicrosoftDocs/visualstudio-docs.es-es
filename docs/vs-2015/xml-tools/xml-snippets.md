---
title: Fragmentos de código XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5bc8946d62f47291a6e0e3f26032589bfdf0de16
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669365"
---
# <a name="xml-snippets"></a>Fragmentos de código XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El editor XML ofrece una característica, denominada *fragmentos XML*, que permite crear archivos XML con mayor rapidez. Los fragmentos XML se pueden reutilizar insertándolos en los archivos. También es posible generar datos XML en un esquema de lenguaje de definición de esquemas XML (XSD).

## <a name="reusable-xml-snippets"></a>Fragmentos XML reutilizables
 El Editor XML incluye muchos fragmentos que abarcan algunas tareas comunes. Esto permite crear archivos XML de forma más sencilla. Por ejemplo, si fuera a crear un esquema XML con los fragmentos "Complex Type Sequence Element" y "Simple Type Element", insertaría el texto XML siguiente en el archivo. Luego, cambiaría el valor `name` de acuerdo con sus necesidades.

```
<xs:element name="name">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="name">
        <xs:simpleType>
          <xs:restriction base="xs:string"></xs:restriction>
        </xs:simpleType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

 Los fragmentos se pueden insertar de dos maneras. El comando **Insertar fragmento** inserta el fragmento de código XML en la posición del cursor. El comando **rodear con** ajusta el fragmento de código XML alrededor del texto seleccionado. Ambos comandos están disponibles en el submenú **IntelliSense** del menú **edición** o en el menú contextual del editor.

 Para obtener más información, vea [Cómo: usar fragmentos de código XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por esquema
 Con el Editor XML también es posible generar un fragmento XML desde un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento.

 Para obtener más información, vea [Cómo: generar un fragmento de código XML a partir de un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML
 Además de los fragmentos de código que se incluyen con [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio de forma predeterminada, también puede crear y usar sus propios fragmentos XML.

 Para obtener más información, vea [Cómo: crear fragmentos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vea también
 [Editor XML](../xml-tools/xml-editor.md)
