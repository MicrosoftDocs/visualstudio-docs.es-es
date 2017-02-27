---
title: "C&#243;mo: crear un subcomponente de fuente para una galer&#237;a privada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fuente Atom, las galerías privadas VSIX"
  - "Galerías privadas VSIX, fuente Atom"
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: crear un subcomponente de fuente para una galer&#237;a privada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede crear un Atom fuente RSS \(\) en una ubicación de intranet que contiene las extensiones y agrega la fuente a **extensiones y actualizaciones** como una galería privada. Para obtener más información, consulta [Galerías privadas](../extensibility/private-galleries.md).  
  
## Crear una Atom fuente  
 Para crear una fuente como una galería privada Atom, primero recopilar sus extensiones \(archivos .vsix\) en una carpeta. Si desea que se puede organizarlos en subcarpetas. También necesitará los siguientes recursos:  
  
-   Un archivo de atom.xml que hace que las extensiones disponibles como una galería privada. Para obtener información acerca de cómo conectar el archivo atom.xml a **extensiones y actualizaciones**, consulte [Galerías privadas](../extensibility/private-galleries.md).  
  
-   Una carpeta que contiene los archivos de imagen que se han extraído de las extensiones \(por ejemplo, capturas de pantalla\). El archivo atom.xml contiene vínculos relativos a estas imágenes para que estén disponibles en **extensiones y actualizaciones**.  
  
 Por ejemplo, suponga que ha recopilado en una carpeta de las dos extensiones siguientes:  
  
-   Template\_Wizard\_239.vsix, que es una plantilla de proyecto VSIX vacía.  
  
-   SelectionHighlight.vsix, que es una herramienta para resaltar todas las instancias de una palabra seleccionada.  
  
 El contenido del archivo atom.xml sería similar al ejemplo siguiente:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?> - <feed xmlns="http://www.w3.org/2005/Atom"> <title type="text" /> <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id> <updated>2011-04-14T21:25:48Z</updated> - <entry> <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id> <title type="text">Highlight all occurrences of selected word</title> <summary type="text">This extends the editor to highlight ….</summary> <published>2011-04-14T14:24:51-07:00</published> <updated>2011-04-14T14:24:22-07:00</updated> - <author> <name>Microsoft</name> </author> <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" /> <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" /> <content type="application/octet-stream" src="SelectionHighlight.vsix" /> - <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010"> <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id> <Version>1.31</Version> <References /> <Rating xsi:nil="true" /> <RatingCount xsi:nil="true" /> <DownloadCount xsi:nil="true" /> </Vsix> </entry> - <entry> <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id> … </entry> </feed>  
  
```  
  
 Observe que las etiquetas de dos vínculo Consulte capturas de pantalla de la carpeta de imágenes generada.  
  
## Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)