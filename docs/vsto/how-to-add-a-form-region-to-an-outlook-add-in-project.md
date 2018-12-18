---
title: 'Cómo: agregar un área de formulario a un proyecto de complemento de Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 875644c10b07eb9c2b338b5a3cdfc827a76a7b34
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549043"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Cómo: agregar un área de formulario a un proyecto de complemento de Outlook
  Crear un área de formulario para extender un formulario de Microsoft Office Outlook estándar o personalizado, mediante el asistente **Nueva área de formulario de Outlook** . Puede crear una nueva área de formulario y diseñar la interfaz de usuario en Visual Studio, o puede importar un área de formulario diseñada en Outlook y agregar el código de Visual Basic o C#.  
  
 Si ha usado un área de formulario de Outlook en otro proyecto de Outlook, puede volver a usarla en el proyecto de complemento de VSTO de Outlook actual mediante el cuadro de diálogo **Agregar elemento existente** . Para obtener más información, consulte [áreas de formulario de Outlook crear](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Agregar un área de formulario nueva a un proyecto de Outlook  
  
1.  En primer lugar, abra o cree un proyecto de complemento VSTO de Outlook en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obtener más información, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  En el **Explorador de soluciones**, seleccione el nodo de proyecto del complemento VSTO de Outlook.  
  
3.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
4.  En el cuadro de diálogo **Agregar nuevo elemento** , seleccione **Área de formularios de Outlook**.  
  
5.  Escriba un nombre para el área de formulario en el cuadro **Nombre** y, a continuación, haga clic en **Agregar**.  
  
     El **área de formulario de NewOutlook** inicia el Asistente para.  
  
6.  En la página **Seleccione cómo desea crear el área de formulario** , seleccione si desea diseñar el área de formulario; para hacer esto, debe arrastrar los controles administrados a un diseñador visual o importar un área de formulario diseñada en Outlook.  
  
    > [!NOTE]  
    >  Si decide importar un área de formulario diseñada en Outlook, debe especificar la ubicación de un almacén de formularios de Outlook (*.ofs*) archivos. Recuerde que no puede agregar controles administrados a un área de formulario que haya diseñado en Outlook; solo puede agregar el código subyacente de la interfaz de usuario. Para obtener más información, consulte [áreas de formulario de Outlook crear](../vsto/creating-outlook-form-regions.md).  
  
7.  En la página **Seleccione el tipo de área de formulario que desea crear** , revise los tipos de área de formulario y seleccione el que más le convenga; a continuación, haga clic en **Siguiente**. Para obtener más información sobre los tipos de área de formulario, vea [áreas de formulario de Outlook crear](../vsto/creating-outlook-form-regions.md).  
  
8.  En la página **Escriba un texto descriptivo y seleccione sus preferencias de presentación** , en el cuadro **Nombre** , escriba un nombre para el área de formulario. En las áreas de formulario de tipo Reemplazo y Reemplazo total , también tiene disponibles los cuadros **Título** y **Descripción** .  
  
     Para obtener información sobre dónde el nombre, el título y la descripción aparecen en Outlook al implementar el área de formulario, vea [áreas de formulario de Outlook crear](../vsto/creating-outlook-form-regions.md).  
  
9. Seleccione uno o más modos de presentación en los que desee que aparezca el área de formulario.  
  
     Todos los tipos de área de formulario pueden aparecer en los inspectores, en el modo de creación (para crear elementos) y en el modo de lectura (para ver elementos). Asimismo, en el panel de lectura también pueden aparecer los tipos de áreas de formulario Adyacente, Reemplazo y Reemplazo total.  
  
10. Haga clic en **Siguiente**.  
  
11. En la página **Identifique las clases de mensaje que mostrarán esta área de formulario** , seleccione las clases de mensaje estándar de Outlook que desee o escriba los nombres de una o más clases de mensaje personalizadas; a continuación, haga clic en **Finalizar**. Para obtener más información, consulte [asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Obtener acceso a un área de formulario en tiempo de ejecución](../vsto/accessing-a-form-region-at-run-time.md)   
 [Soluciones de Outlook](../vsto/outlook-solutions.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Directrices para crean áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)  
  