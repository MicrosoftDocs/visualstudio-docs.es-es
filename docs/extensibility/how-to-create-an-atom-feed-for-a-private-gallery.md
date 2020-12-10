---
title: 'Cómo: crear una fuente Atom para una galería privada | Microsoft Docs'
description: Puede crear una fuente Atom (RSS) en una ubicación de la intranet que contenga extensiones y agregar la fuente a extensiones y actualizaciones como una galería privada.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 833d75d7dfd18e863664e6d3d17d65a4e08b4d77
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994152"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Cómo: crear una fuente Atom para una galería privada
Puede crear una fuente Atom (RSS) en una ubicación de la intranet que contenga extensiones y agregar la fuente a **extensiones y actualizaciones** como una galería privada. Para más información, consulte [Private galleries](../extensibility/private-galleries.md) (Galerías privadas).

## <a name="create-an-atom-feed"></a>Creación de una fuente Atom
 Para crear una fuente Atom como una galería privada, primero debe recopilar las extensiones (archivos *. vsix* ) en una carpeta. Puede organizarlos en subcarpetas si lo desea. También necesitará los siguientes recursos:

- Un archivo *atom.xml* que hace que las extensiones estén disponibles como una galería privada. Para obtener información sobre cómo conectar el archivo de *atom.xml* a **extensiones y actualizaciones**, vea [galerías privadas](../extensibility/private-galleries.md).

- Una carpeta que contiene los archivos de imagen extraídos de las extensiones (por ejemplo, capturas de pantalla). El archivo *atom.xml* contiene vínculos relativos a estas imágenes para que estén disponibles en **extensiones y actualizaciones**.

  Por ejemplo, suponga que ha recopilado las dos extensiones siguientes en una carpeta:

- *Template_Wizard_239. vsix*, que es una plantilla de proyecto de VSIX vacía.

- *SelectionHighlight. vsix*, que es una herramienta para resaltar todas las instancias de una palabra seleccionada.

  El contenido del archivo *atom.xml* sería similar al ejemplo siguiente:

```xml
<?xml version="1.0" encoding="UTF-8"?>
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
    <Vsix xmlns="http://schemas.microsoft.com/developer/vsx-syndication-schema/2010" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
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

 Tenga en cuenta que las dos etiquetas de vínculo hacen referencia a las capturas de pantalla de la carpeta de imágenes generada.

## <a name="see-also"></a>Consulte también
- [Galerías privadas](../extensibility/private-galleries.md)
