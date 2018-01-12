---
title: Fragmentos XML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9a419d738943f780ddb6077978242ac08ff91d36
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2018
---
# <a name="xml-snippets"></a>Fragmentos de código XML
El Editor XML ofrece una característica denominada *fragmentos XML*, que le permite compilar archivos XML con más rapidez. Los fragmentos XML se pueden reutilizar insertándolos en los archivos. También es posible generar datos XML en un esquema de lenguaje de definición de esquemas XML (XSD).  
  
## <a name="reusable-xml-snippets"></a>Fragmentos XML reutilizables  
 El Editor XML incluye muchos fragmentos que abarcan algunas tareas comunes. Esto permite crear archivos XML de forma más sencilla. Por ejemplo, si fuera a crear un esquema XML con los fragmentos "Complex Type Sequence Element" y "Simple Type Element", insertaría el texto XML siguiente en el archivo. Luego, cambiaría el valor `name` de acuerdo con sus necesidades.  
  
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
  
 Los fragmentos se pueden insertar de dos maneras. El **Insertar fragmento de código** comando inserta el fragmento XML en la posición del cursor. El **rodear con** comando ajusta el fragmento XML alrededor del texto seleccionado. Ambos comandos están disponibles desde el **IntelliSense** submenú en el **editar** menú, o en el menú contextual de editor.  
  
 Para obtener más información, consulte [Cómo: utilizar fragmentos de código XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por esquema  
 Con el Editor XML también es posible generar un fragmento XML desde un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento.  
  
 Para obtener más información, consulte [Cómo: generar un XML desde un esquema XML del fragmento](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML  
 Además de los fragmentos de código que se incluyen con [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio de forma predeterminada, también puede crear y utilizar sus propios fragmentos XML.  
  
 Para obtener más información, consulte [Cómo: crear fragmentos XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)