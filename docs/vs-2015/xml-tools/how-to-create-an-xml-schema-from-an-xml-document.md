---
title: Filtrar Crear un esquema XML de un documento XML | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 50e601d03901484ed6e759fb336b1effa5b37841
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995350"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Filtrar Crear un esquema XML a partir de un documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:  
  
- Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.  
  
- Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.  
  
- Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.  
  
  Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.  
  
  Para obtener más información acerca del motor de inferencia del esquema, vea [deducción de esquema XML](http://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Para crear un esquema XML  
  
1.  Cargue un documento de instancia XML en el Editor XML.  
  
2.  Haga clic en el **Create Schema** botón desde la **barra de herramientas**.  
  
     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML. Cada esquema se abre como un archivo de varios temporal.  
  
     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.  
  
    > [!NOTE]
    >  El **Create Schema** comando también está disponible en el menú contextual del Editor XML y, en el **XML** menú.  
  
## <a name="see-also"></a>Vea también  
 [Editor XML](../xml-tools/xml-editor.md)
