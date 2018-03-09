---
title: "Cómo: crear una Atom fuente de distribución para una galería privada | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3b966aa30fa2e7e9eae07b56c1a578f9688772a0
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/08/2018
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Cómo: crear una Atom fuente de distribución para una galería privada
Puede crear una Atom () fuente RSS en una ubicación de intranet que contiene las extensiones y agrega la fuente a **extensiones y actualizaciones** como galería privada. Para más información, vea [Private Galleries](../extensibility/private-galleries.md) (Galerías privadas).  
  
## <a name="creating-an-atom-feed"></a>Crear una Atom fuente  
 Para crear una fuente como galería privada Atom, se recopilan primero sus extensiones (archivos .vsix) en una carpeta. Puede organizarlos en subcarpetas si desea. También necesitará los siguientes recursos:  
  
-   Un archivo atom.xml que pone a disposición las extensiones como galería privada. Para obtener información sobre cómo conectar el archivo atom.xml **extensiones y actualizaciones**, consulte [ensamblados privados](../extensibility/private-galleries.md).  
  
-   Una carpeta que contiene los archivos de imagen que se han extraído de las extensiones (por ejemplo, las capturas de pantalla). El archivo atom.xml contiene vínculos relativos a estas imágenes para que estén disponibles en **extensiones y actualizaciones**.  
  
 Por ejemplo, supongamos que ha recopilado las siguientes dos extensiones en una carpeta:  
  
-   Template_Wizard_239.vsix, que es una plantilla de proyecto VSIX vacía.  
  
-   SelectionHighlight.vsix, que es una herramienta para resaltar todas las instancias de una palabra seleccionada.  
  
 El contenido del archivo atom.xml sería algo parecido en el ejemplo siguiente:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<feed xmlns="http://www.w3.org/2005/Atom">  
<title type="text" />   
<id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
<updated>2011-04-14T21:25:48Z</updated>   
<entry>  
<id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
<title type="text">Highlight all occurrences of selected word</title>   
<summary type="text">This extends the editor to highlight ....</summary>   
<published>2011-04-14T14:24:51-07:00</published>   
<updated>2011-04-14T14:24:22-07:00</updated>   
<author>  
<name>Microsoft</name>   
</author>  
<link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
<link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
<content type="application/octet-stream" src="SelectionHighlight.vsix" />   
<Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
<Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
<Version>1.31</Version>   
<References />   
<Rating xsi:nil="true" />   
<RatingCount xsi:nil="true" />   
<DownloadCount xsi:nil="true" />   
</Vsix>  
</entry>  
<entry>  
<id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
...  
</entry>  
</feed>
```  
  
 Tenga en cuenta que las etiquetas de dos vínculo hacen referencia a las capturas de pantalla en la carpeta de imágenes generada.  
  
## <a name="see-also"></a>Vea también  
 [Galerías privadas](../extensibility/private-galleries.md)
