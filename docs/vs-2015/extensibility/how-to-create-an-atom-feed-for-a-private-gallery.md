---
title: 'Cómo: crear una fuente Atom para una galería privada | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6d4ba78028774e8fbf8e281afa2855781dab43a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204210"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Creación de una fuente Atom para una galería privada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear una fuente Atom (RSS) en una ubicación de la intranet que contenga extensiones y agregar la fuente a **extensiones y actualizaciones** como una galería privada. Para obtener más información, vea [galerías privadas](../extensibility/private-galleries.md).  
  
## <a name="creating-an-atom-feed"></a>Crear una fuente Atom  
 Para crear una fuente Atom como una galería privada, primero debe recopilar las extensiones (archivos. vsix) en una carpeta. Puede organizarlos en subcarpetas si lo desea. También necesitará los siguientes recursos:  
  
- Un archivo atom.xml que hace que las extensiones estén disponibles como una galería privada. Para obtener información sobre cómo conectar el archivo de atom.xml a **extensiones y actualizaciones**, vea [galerías privadas](../extensibility/private-galleries.md).  
  
- Una carpeta que contiene los archivos de imagen extraídos de las extensiones (por ejemplo, capturas de pantalla). El archivo atom.xml contiene vínculos relativos a estas imágenes para que estén disponibles en **extensiones y actualizaciones**.  
  
  Por ejemplo, suponga que ha recopilado las dos extensiones siguientes en una carpeta:  
  
- Template_Wizard_239. vsix, que es una plantilla de proyecto de VSIX vacía.  
  
- SelectionHighlight. vsix, que es una herramienta para resaltar todas las instancias de una palabra seleccionada.  
  
  El contenido del archivo atom.xml sería similar al ejemplo siguiente:  
  
```  
  <?xml version="1.0" encoding="utf-8" ?>   
- <feed xmlns="http://www.w3.org/2005/Atom">  
  <title type="text" />   
  <id>uuid:bcecded5-97c8-4d24-96f1-7d9e16652433;id=1</id>   
  <updated>2011-04-14T21:25:48Z</updated>   
- <entry>  
  <id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</id>   
  <title type="text">Highlight all occurrences of selected word</title>   
  <summary type="text">This extends the editor to highlight ….</summary>   
  <published>2011-04-14T14:24:51-07:00</published>   
  <updated>2011-04-14T14:24:22-07:00</updated>   
- <author>  
  <name>Microsoft</name>   
  </author>  
  <link rel="icon" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_Icon_SelectionHighlightIcon.jpg" />   
  <link rel="previewimage" href="VSIXImages/SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa_PreviewImage_SelectionHighlight.jpg" />   
  <content type="application/octet-stream" src="SelectionHighlight.vsix" />   
- <Vsix xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010">  
  <Id>SelectionHighlight..a14874d2-8199-4a60-af8a-11d6447813aa</Id>   
  <Version>1.31</Version>   
  <References />   
  <Rating xsi:nil="true" />   
  <RatingCount xsi:nil="true" />   
  <DownloadCount xsi:nil="true" />   
  </Vsix>  
  </entry>  
- <entry>  
  <id>Template_Wizard_239.Microsoft.3b38a7e3-5cbc-4389-a92a-d82tyc2ed592</id>   
  …  
  </entry>  
  </feed>  
  
```  
  
 Tenga en cuenta que las dos etiquetas de vínculo hacen referencia a las capturas de pantalla de la carpeta de imágenes generada.  
  
## <a name="see-also"></a>Consulte también  
 [Galerías privadas](../extensibility/private-galleries.md)
