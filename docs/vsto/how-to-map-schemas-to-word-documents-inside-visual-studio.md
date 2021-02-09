---
title: 'Cómo: asignar esquemas a documentos de Word en Visual Studio'
description: Obtenga información sobre cómo puede asignar un esquema XML a un documento de Microsoft Office Word mientras el documento está abierto en Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900923"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Cómo: asignar esquemas a documentos de Word en Visual Studio
  **Importante** La información configurada en este tema con respecto a Microsoft Word se presenta exclusivamente para la ventaja y el uso de las personas y organizaciones que se encuentran fuera del Estados Unidos y de sus territorios, o bien el desarrollo de programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft antes de la 2010 de enero, cuando Microsoft quitó una implementación de funcionalidad específica relacionada con XML personalizado de Es posible que la información relativa a Microsoft Word no sea leída ni utilizada por personas u organizaciones en el Estados Unidos ni en sus territorios que utilicen o desarrollen programas que se ejecutan en, productos de Microsoft Word con licencia de Microsoft a partir del 10 de enero de 2010; Estos productos no se comportarán igual que los productos con licencia antes de esa fecha o adquiridos y con licencia para usarlos fuera del Estados Unidos.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Puede asignar un esquema XML a un documento mientras el documento está abierto en Visual Studio. Utilice las mismas Microsoft Office herramientas de Word que usa cuando el documento está abierto fuera de Visual Studio. El proyecto de Office crea los mismos objetos si asigna el esquema al documento antes o después de crear la solución de Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Para asignar un esquema XML a un documento de Word en Visual Studio

1. Abra el proyecto de documento o plantilla de Word dentro de Visual Studio.

2. Haga clic en el documento para pasar el foco al diseñador.

3. En la cinta de opciones, haga clic en la pestaña **desarrollador** .

    > [!NOTE]
    > Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. En el grupo **XML** , haga clic en **esquema**.

     Se abrirá el cuadro de diálogo **plantillas y complementos** .

5. Haga clic en la pestaña **esquema XML** .

6. Haga clic en **Agregar esquema**.

     Se abre el cuadro de diálogo **Agregar esquema** .

7. Busque el archivo de esquema, selecciónelo y, a continuación, haga clic en **abrir**.

     Se abrirá el cuadro de diálogo **configuración de esquema** .

8. Asigne un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.

9. Haga clic en **OK**.

     Se abre la ventana **estructura XML** .

10. Arrastre los elementos desde la ventana **estructura XML** hasta los lugares del documento donde desea que se creen los controles correspondientes.

## <a name="see-also"></a>Vea también
- [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
