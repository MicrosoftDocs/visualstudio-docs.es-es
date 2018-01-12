---
title: "Cómo: asignar esquemas a documentos de Word en Visual Studio | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 65ecd3adbeb6f554a901345c2fa5dbf8359a1428
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Cómo: Asignar esquemas a documentos de Word en Visual Studio
  **Importante** la información que figura en este tema con respecto a Microsoft Word está presentado exclusivamente para el beneficio y el uso de personas y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o que está usando, o del desarrollo programas que se ejecutan en, productos de Microsoft Word que se autoriza el uso de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de funcionalidad concreta relacionada con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede leer o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que están usando o desarrollar programas que se ejecutan en productos de Microsoft Word que se usan bajo licencia Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Puede asignar un esquema XML a un documento mientras el documento está abierto en Visual Studio. Use las mismas herramientas de Microsoft Office Word que utilizan cuando el documento está abierto fuera de Visual Studio. El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema al documento antes o después de crear la solución de Word.  
  
### <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Para asignar un esquema XML a un documento de Word en Visual Studio  
  
1.  Abra el proyecto de documento o plantilla de Word en Visual Studio.  
  
2.  Haga clic en el documento que se va a mover el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en la pestaña **Desarrollador** .  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulta [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el **XML** grupo, haga clic en **esquema**.  
  
     El **plantillas y complementos** abre el cuadro de diálogo.  
  
5.  Haga clic en el **esquema XML** ficha.  
  
6.  Haga clic en **Agregar esquema**.  
  
     El **Agregar esquema** abre el cuadro de diálogo.  
  
7.  Vaya al archivo de esquema, selecciónelo y, a continuación, haga clic en **abiertos**.  
  
     El **configuración del esquema** abre el cuadro de diálogo.  
  
8.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
9. Haga clic en **Aceptar**.  
  
     El **estructura XML** abre la ventana.  
  
10. Arrastre elementos desde la **estructura XML** ventana hasta los lugares en el documento donde desea que los controles correspondientes que se va a crear.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: asignar esquemas a hojas de cálculo dentro de Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  