---
title: 'Cómo: crear un esquema XML a partir de un documento XML | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9b19421bf9cb9d974a837f557d8b75ac4d5ba89c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Cómo: Crear un esquema XML a partir de un documento XML
El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:  
  
-   Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.  
  
-   Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.  
  
-   Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.  
  
Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.  
  
Para obtener más información acerca del motor de inferencia del esquema, consulte [deducir un esquema XML](/dotnet/standard/data/xml/inferring-an-xml-schema).  
  
### <a name="to-create-an-xml-schema"></a>Para crear un esquema XML  
  
1.  Cargue un documento de instancia XML en el Editor XML.  
  
2.  Haga clic en el **Create Schema** botón desde la **barra de herramientas**.  
  
     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML. Cada esquema se abre como un archivo de varios temporal.  
  
     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.  
  
    > [!NOTE]
    >  El **Create Schema** comando también está disponible en el menú contextual del Editor XML y, en la **XML** menú.  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)