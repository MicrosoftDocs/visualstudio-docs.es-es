---
title: 'Cómo: crear un esquema XML a partir de un documento XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670927"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Cómo: Crear un esquema XML a partir de un documento XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Editor XML permite crear un esquema de lenguaje de definición de esquemas XML (XSD) a partir de un documento XML. El documento de instancia XML determina cómo se genera el esquema de la siguiente manera:

- Si el documento XML no tiene asociado un esquema o una definición de tipo de documento (DTD), los datos del documento XML se utilizan para inferir un nuevo esquema XML.

- Si el documento XML contiene una DTD asociada, la DTD externa y el subconjunto interno se convierten en un esquema XML correspondiente.

- Si el documento XML contiene un esquema reducido de datos XML (XDR) alineado, el esquema XDR se convierte en un esquema XML correspondiente.

  Los esquemas creados se utilizan luego para proporcionar IntelliSense en el documento XML.

  Para obtener más información sobre el motor de inferencia de esquema, vea [inferir un esquema XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Para crear un esquema XML

1. Cargue un documento de instancia XML en el Editor XML.

2. Haga clic en el botón **crear esquema** de la **barra de herramientas**.

     Se crea un documento de esquema XML, que se abre para cada espacio de nombres hallado en el documento de instancia XML. Cada esquema se abre como un archivo de varios temporal.

     Los esquemas se pueden guardar en un disco, agregarse a un proyecto o descartarse.

    > [!NOTE]
    > El comando **crear esquema** también está disponible en el menú contextual del editor XML y en el menú **XML** .

## <a name="see-also"></a>Vea también
 [Editor XML](../xml-tools/xml-editor.md)
