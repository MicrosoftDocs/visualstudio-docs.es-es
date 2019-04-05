---
title: Fragmentos XML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c6c3155ee65031b57ec70cc7f22ed53cdef67ebf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58997321"
---
# <a name="xml-snippets"></a>Fragmentos de código XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML ofrece una característica denominada *fragmentos XML*, que le permite compilar archivos XML con mayor rapidez. Los fragmentos XML se pueden reutilizar insertándolos en los archivos. También es posible generar datos XML en un esquema de lenguaje de definición de esquemas XML (XSD).  
  
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
  
 Los fragmentos se pueden insertar de dos maneras. El **Insertar fragmento de código** comando inserta el fragmento XML en la posición del cursor. El **rodear con** comando encapsula el fragmento XML alrededor del texto seleccionado. Ambos comandos están disponibles desde el **IntelliSense** submenú en el **editar** menú, o desde el menú contextual del editor.  
  
 Para obtener más información, vea [Cómo: Utilizar fragmentos XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por esquema  
 Con el Editor XML también es posible generar un fragmento XML desde un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento.  
  
 Para obtener más información, vea [Cómo: Generar un fragmento XML desde un esquema XML](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML  
 Además de los fragmentos de código que se incluyen con [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio de forma predeterminada, también puede crear y utilizar sus propios fragmentos de XML.  
  
 Para obtener más información, vea [Cómo: Crear fragmentos XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)
