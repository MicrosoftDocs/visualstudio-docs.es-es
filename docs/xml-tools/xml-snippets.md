---
title: fragmentos XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66736431b295f974bda1ca855d88cd5f5f868e7d
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526160"
---
# <a name="xml-snippets"></a>fragmentos XML

El editor XML ofrece una característica denominada *fragmentos XML*, que le permite compilar archivos XML con mayor rapidez. Los fragmentos XML se pueden reutilizar insertándolos en los archivos. También puede generar datos XML en un esquema XML schema definition language (XSD).

## <a name="reusable-xml-snippets"></a>Fragmentos XML reutilizables

El editor XML incluye muchos fragmentos que abarcan algunas tareas comunes. Esto permite crear archivos XML de forma más sencilla. Por ejemplo, si fuera a crear un esquema XML, utilizando los fragmentos "Complex Type Sequence Element" y "Simple Type Element" inserta el texto XML siguiente al archivo. Luego, cambiaría el valor `name` de acuerdo con sus necesidades.

```xml
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

Los fragmentos se pueden insertar de dos maneras. El **Insertar fragmento de código** comando inserta el fragmento XML en la posición del cursor. El **rodear con** comando encapsula el fragmento XML alrededor del texto seleccionado. Ambos comandos están disponibles desde el **IntelliSense** submenú en el **editar** menú, o en el menú contextual en el editor.

Para obtener más información, vea [Cómo: Utilizar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por esquema

El editor XML también tiene la capacidad de generar un fragmento XML desde un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento. Para obtener más información, vea [Cómo: Generar un fragmento XML desde un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML

Además de los fragmentos de código que se incluyen con Visual Studio de forma predeterminada, también puede crear y utilizar sus propios fragmentos de XML. Para obtener más información, vea [Cómo: Crear fragmentos XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vea también

- [Fragmentos de código en Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)