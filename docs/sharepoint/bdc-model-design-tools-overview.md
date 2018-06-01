---
title: Información general de herramientas de diseño del modelo BDC | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 11469e76464cf4177d581705004bf640d71c43a1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691484"
---
# <a name="bdc-model-design-tools-overview"></a>Información general de herramientas del diseño de modelo BDC
  Puede diseñar un modelo de conectividad de datos profesionales (BDC) mediante el Diseñador de BDC, el **detalles del método de BDC** ventana y el **Explorador de BDC**.  
  
 El **Explorador de BDC** le permite examinar el modelo, buscar en el modelo y definir los descriptores de tipo.  
  
## <a name="bdc-designer"></a>Diseñador de BDC
 El Diseñador de BDC permite definir las entidades en el modelo y organizar visualmente sus relaciones entre sí. Use el Diseñador de BDC para realizar las tareas siguientes:  
  
-   Agregue las entidades en el modelo.  
  
-   Quitar entidades del modelo.  
  
-   Definir relaciones entre entidades.  
  
 Para abrir el Diseñador de BDC, haga doble clic en el archivo de modelo en el proyecto, o abra el menú contextual para el archivo de modelo y, a continuación, elija **abrir**. Agregar una entidad al modelo arrastrando o copiando una **entidad** desde el **cuadro de herramientas** en el diseñador. Para crear una asociación entre dos entidades, elija la **asociación** controlar en el **cuadro de herramientas**, elija la primera entidad y, a continuación, elija la segunda entidad.  
  
## <a name="bdc-method-details-window"></a>Ventana de detalles del método BDC
 Use la **detalles del método de BDC** ventana para definir los parámetros, las instancias y descriptores de filtro de un método.  
  
 Puede generar rápidamente métodos Finder, Finder específico, creador, Updater y Deleter en la **detalles del método de BDC** ventana. Cuando se generan estos métodos, Visual Studio agrega metadatos, como parámetros, instancias y descriptores de tipos, en el método. Puede modificar estos metadatos para satisfacer su escenario concreto.  
  
 Para abrir el **detalles del método de BDC** ventana, en la barra de menús, elija **vista**, **otras ventanas**, **detalles del método de BDC**.  
  
 Para ver los métodos en el **detalles del método de BDC** ventana, seleccione la entidad en el Diseñador de BDC. Los métodos de la entidad seleccionada aparecen en la **detalles del método de BDC** ventana. Si no elige una entidad en el Diseñador de BDC, el **detalles del método de BDC** ventana no muestra ninguna información.  
  
 Expandir o contraer nodos en el **detalles del método de BDC** ventana para definir parámetros, instancias y descriptores de filtro. Use la **Explorador de BDC** para definir descriptores de tipo.  
  
## <a name="bdc-explorer"></a>Explorador de BDC
 El **Explorador de BDC** muestra los elementos que componen el modelo. Para abrir el **Explorador de BDC**, en la barra de menús, elija **vista**, **otras ventanas**, **Explorador de BDC**. Para examinar el modelo, expanda los nodos situados en la **Explorador de BDC**. Cada nodo representa un elemento en el XML del archivo del modelo.  
  
 Al seleccionar nodos en el **Explorador de BDC**, las propiedades de cada nodo que elija aparecen en la **propiedades** ventana. Muchas de estas propiedades corresponden a los atributos en el archivo de modelo. Puede buscar el modelo mediante el cuadro de búsqueda en la parte superior de la **Explorador de BDC**.  
  
> [!NOTE]  
>  El **Explorador de BDC** no muestra identificadores, propiedades personalizadas, las cadenas localizadas, grupos de asociaciones, acciones, descriptores de filtro, listas de control de acción y los valores de parámetro predeterminados.  
  
### <a name="define-type-descriptors"></a>Definir descriptores de tipo
 Use la **Explorador de BDC** para definir descriptores de tipo. El Explorador de BDC permite definir un descriptor de tipo una vez y, a continuación, volver a usar ese descriptor de tipo en otro lugar en el modelo. Para lograr esto, copie un descriptor de tipos y péguelo en cualquier otro parámetro o descriptor de tipos.  
  
> [!NOTE]  
>  Cambios en un descriptor de tipos original no afectan a las copias de ese descriptor de tipos.  
  
 Para obtener más información, consulte [Cómo: definir el Descriptor de tipo de un parámetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Vea también
 [Cómo: crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Crear una asociación entre entidades](../sharepoint/creating-an-association-between-entities.md)   
 [Tutorial: Crear una lista externa en SharePoint con datos profesionales](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
 