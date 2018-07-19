---
title: 'Cómo: asignar esquemas a documentos de Word en Visual Studio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e3bec0437fb9bcd55821e27b22b118430024f751
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255436"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Cómo: asignar esquemas a documentos de Word en Visual Studio
  **Importante** la información en este tema con respecto a Microsoft Word se presenta exclusivamente para el uso y disfrute de individuos y organizaciones que se encuentran fuera de Estados Unidos y sus territorios o quién está usando o desarrollo programas que se ejecutan en, los productos de Microsoft Word que se licencia de Microsoft antes de enero de 2010, cuando Microsoft quita una implementación de la funcionalidad concreta relacionadas con XML personalizado de Microsoft Word. Esta información con respecto a Microsoft Word no puede ser leída o utilizada por personas u organizaciones en Estados Unidos o en sus territorios que utiliza, o desarrollar programas que se ejecutan en los productos de Microsoft Word que se licencia de Microsoft después de 10 de enero de 2010 ; los productos no comportarán igual que los productos con licencia antes de esa fecha o adquirido y con licencia para su uso fuera de Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Puede asignar un esquema XML a un documento mientras el documento está abierto en Visual Studio. Use las mismas herramientas de Microsoft Office Word que usan cuando el documento está abierto fuera de Visual Studio. El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema para el documento antes o después de crear la solución de Word.  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Para asignar un esquema XML a un documento de Word en Visual Studio  
  
1.  Abra el proyecto de documento o plantilla de Word en Visual Studio.  
  
2.  Haga clic en el documento para mover el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en el **Developer** ficha.  
  
    > [!NOTE]  
    >  Si la pestaña **Desarrollador** no está visible, primero debe mostrarla. Para obtener más información, consulte [Cómo: mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el **XML** grupo, haga clic en **esquema**.  
  
     El **plantillas y complementos** abre el cuadro de diálogo.  
  
5.  Haga clic en el **esquema XML** ficha.  
  
6.  Haga clic en **Agregar esquema**.  
  
     El **Agregar esquema** abre el cuadro de diálogo.  
  
7.  Busque el archivo de esquema, selecciónelo y, a continuación, haga clic en **abierto**.  
  
     El **configuración del esquema** abre el cuadro de diálogo.  
  
8.  Asignar un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
9. Haga clic en **Aceptar**.  
  
     El **estructura XML** abre la ventana.  
  
10. Arrastre elementos desde el **estructura XML** ventana a los lugares en el documento donde desea que los controles correspondientes a crearse.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Esquemas y datos en las personalizaciones de nivel de documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  