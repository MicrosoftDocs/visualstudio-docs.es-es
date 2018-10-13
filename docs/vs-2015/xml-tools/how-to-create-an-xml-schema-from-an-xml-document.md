---
title: 'Cómo: crear un esquema XML de un documento XML | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d5d2e4cc78ee79502c4f2e10b2343fa0723006b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181278"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Cómo: Crear un esquema XML a partir de un documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:  
  
-   Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.  
  
-   Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.  
  
-   Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.  
  
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



