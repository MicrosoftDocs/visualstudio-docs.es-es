---
title: 'Cómo: localizar una característica | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08756ce33d97e156d63fd873c63d4d6fc282285b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-a-feature"></a>Cómo: Localizar una característica
  De forma predeterminada, las descripciones y títulos de estas características utilizan valores de cadena codificados de forma rígida. Para localizar el título de la característica y la descripción, reemplace las cadenas con expresiones que hacen referencia a los recursos localizados.  
  
## <a name="localizing-a-feature"></a>Localizar una característica  
  
#### <a name="to-localize-a-feature"></a>Para localizar una característica  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **Feature1** nodo y, a continuación, elija **Agregar recurso de características**.  
  
2.  En el **Agregar recurso** diálogo cuadro, elija **todos los idiomas** en la lista según la referencia cultural para el archivo de recursos de característica de idioma predeterminado.  
  
3.  Repita el paso anterior para cada idioma localizado, elegir los idiomas de su elección para la característica localizada en archivos de recursos.  
  
     Se crean archivos de recursos de características independientes: uno para el idioma predeterminado y otro para cada uno de los idiomas que desea admitir localizados.  
  
4.  Abra cada archivo de recursos en el Editor de recursos y, a continuación, especificar todos los valores de los identificadores de cadena y sus valores.  
  
     Por ejemplo, en el archivo de recursos de característica predeterminado, escriba un identificador de cadena de **título** con un valor de **My Feature Title**, y un segundo identificador de cadena del **descripción** con un valor de **Mi descripción de la característica**. Para cada archivo de recursos localizado, use la misma cadena de identificadores utilizados en el recurso de característica predeterminado, pero especifique las cadenas localizadas para los valores.  
  
5.  Después de escribir todos los valores de recursos, abra el menú contextual para la característica (por ejemplo, Feature1.feature) y, a continuación, elija **Ver diseñador** para abrir la característica en el Diseñador de características.  
  
6.  Para localizar el **título** y **descripción** campos de la característica, use el siguiente formato para especificar los valores en sus cuadros:  
  
     `$Resources:` *Identificador de cadena*  
  
     Por ejemplo, escriba $Resources:**título** en el **título de la característica** cuadro y $Resources:**descripción** en el **descripción de la característica** cuadro .  
  
     Los identificadores de cadena deben coincidir con los que se usan en los archivos de recursos.  
  
7.  Elija la tecla F5 para compilar y ejecutar la aplicación.  
  
8.  En SharePoint, abra el **acciones del sitio** menú, elija **configuración del sitio**y, a continuación, en la **acciones del sitio** sección elija la **administrar las características del sitio** vínculo.  
  
9. En SharePoint, cambie el idioma de presentación predeterminado.  
  
     El título de la característica localizado y la descripción aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## <a name="see-also"></a>Vea también  
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
  
  