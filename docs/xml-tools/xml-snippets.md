---
title: fragmentos XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2f2bcdd0c28d7b4b99c92d3346b32ed34aa92a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592326"
---
# <a name="xml-snippets"></a>fragmentos XML

El editor XML ofrece una característica, denominada *fragmentos XML*, que permite crear archivos XML con mayor rapidez. Los fragmentos XML se pueden reutilizar insertándolos en los archivos. También puede generar datos XML basados en un esquema del lenguaje de definición de esquemas XML (XSD).

## <a name="reusable-xml-snippets"></a>Fragmentos XML reutilizables

El editor XML incluye muchos fragmentos de código que cubren algunas tareas comunes. Esto permite crear archivos XML de forma más sencilla. Por ejemplo, si creara un esquema XML, mediante los fragmentos de código "elemento de secuencia de tipo complejo" y "elemento de tipo simple" se inserta el siguiente texto XML en el archivo. Luego, cambiaría el valor `name` de acuerdo con sus necesidades.

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

Los fragmentos se pueden insertar de dos maneras. El comando **Insertar fragmento** inserta el fragmento de código XML en la posición del cursor. El comando **rodear con** ajusta el fragmento de código XML alrededor del texto seleccionado. Ambos comandos están disponibles en el submenú **IntelliSense** del menú **edición** o en el menú contextual del editor.

Para obtener más información, vea [Cómo: usar fragmentos de código XML](../xml-tools/how-to-use-xml-snippets.md).

## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por el esquema

El editor XML también tiene la capacidad de generar un fragmento de código XML a partir de un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento. Para obtener más información, vea [Cómo: generar un fragmento de código XML a partir de un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).

## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML

Además de los fragmentos de código que se incluyen con Visual Studio de forma predeterminada, también puede crear y usar sus propios fragmentos XML. Para obtener más información, vea [Cómo: crear fragmentos de código XML](../xml-tools/how-to-create-xml-snippets.md).

## <a name="see-also"></a>Vea también

- [Fragmentos de código en Visual Studio](../ide/code-snippets.md)
- [Editor XML](../xml-tools/xml-editor.md)
