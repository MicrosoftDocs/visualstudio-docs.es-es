---
title: 'Cómo: Crear una alimentación de átomos para una galería privada ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Atom feed, VSIX private galleries
- VSIX private galleries, Atom feed
ms.assetid: 5897f538-9c41-486f-97d9-a1976d20d9fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72fbf2d3973ffd84de1cf6f33788c43511c3ce4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711008"
---
# <a name="how-to-create-an-atom-feed-for-a-private-gallery"></a>Cómo: Crear un feed Atom para una galería privada
Puede crear una fuente Atom (RSS) en una ubicación de intranet que contenga extensiones y agregar la fuente a **Extensiones y actualizaciones** como una galería privada. Para más información, consulte [Private galleries](../extensibility/private-galleries.md) (Galerías privadas).

## <a name="create-an-atom-feed"></a>Crear una alimentación atom
 Para crear una fuente Atom como una galería privada, primero debe recopilar las extensiones (archivos *.vsix)* en una carpeta. Puede organizarlos en subcarpetas si lo desea. También necesitará los siguientes recursos:

- Un archivo *atom.xml* que hace que las extensiones estén disponibles como una galería privada. Para obtener información sobre cómo conectar el archivo *atom.xml* a **Extensiones y actualizaciones**, consulte [Galerías privadas](../extensibility/private-galleries.md).

- Carpeta que contiene los archivos de imagen extraídos de las extensiones (por ejemplo, capturas de pantalla). El archivo *atom.xml* contiene vínculos relativos a estas imágenes para que estén disponibles en **Extensiones y actualizaciones**.

  Por ejemplo, supongamos que ha recopilado las dos extensiones siguientes en una carpeta:

- *Template_Wizard_239.vsix*, que es una plantilla de proyecto VSIX vacía.

- *SelectionHighlight.vsix*, que es una herramienta para resaltar todas las instancias de una palabra seleccionada.

  El contenido del archivo *atom.xml* se parecería al siguiente ejemplo:

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

 Observe que las dos etiquetas de vínculo hacen referencia a capturas de pantalla en la carpeta generada de imágenes.

## <a name="see-also"></a>Vea también
- [Galerías privadas](../extensibility/private-galleries.md)
