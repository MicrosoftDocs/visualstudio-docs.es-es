---
title: "C&#243;mo: Crear un esquema XML a partir de un documento XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Crear un esquema XML a partir de un documento XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML \(XSD\) a partir de un documento XML.El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:  
  
-   Si el documento XML no tiene asociado un esquema o una definición de tipo de documento \(DTD\), los datos del documento XML se utilizan para inferir un nuevo esquema XML.  
  
-   Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.  
  
-   Si el documento XML contiene un esquema reducido de datos XML \(XDR\) alineado, el esquema XDR se convierte en un esquema XML correspondiente.  
  
 Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.  
  
 Para obtener más información acerca del motor de referencia de esquemas, vea [Deducción de esquema XML](../Topic/Inferring%20an%20XML%20Schema.md).  
  
### Para crear un esquema XML  
  
1.  Cargue un documento de instancia XML en el Editor XML.  
  
2.  Haga clic en el botón **Crear esquema** de la **Barra de herramientas**.  
  
     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML.Cada esquema se abre como un archivo de varios temporal.  
  
     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.  
  
    > [!NOTE]
    >  El comando **Crear esquema** se encuentra también disponible desde el menú contextual del Editor XML y en el menú **XML**.  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)