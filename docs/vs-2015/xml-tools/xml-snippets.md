---
title: Fragmentos XML | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bae360d1aea43006138397b3bed2857a2b1dad59
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582418"
---
# <a name="xml-snippets"></a>Fragmentos de código XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [fragmentos XML](https://docs.microsoft.com/visualstudio/xml-tools/xml-snippets).  
  
  
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
  
 Para obtener más información, consulte [Cómo: usar fragmentos de XML](../xml-tools/how-to-use-xml-snippets.md).  
  
## <a name="schema-generated-xml-snippets"></a>Fragmentos XML generados por esquema  
 Con el Editor XML también es posible generar un fragmento XML desde un esquema XML. Esta característica permite llenar un elemento con elementos XML generados a partir de la información de esquema de ese elemento.  
  
 Para obtener más información, consulte [Cómo: generar un XML desde un esquema XML del fragmento](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md).  
  
## <a name="create-new-xml-snippets"></a>Crear nuevos fragmentos XML  
 Además de los fragmentos de código que se incluyen con [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual Studio de forma predeterminada, también puede crear y utilizar sus propios fragmentos de XML.  
  
 Para obtener más información, consulte [Cómo: crear fragmentos XML](../xml-tools/how-to-create-xml-snippets.md).  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)



