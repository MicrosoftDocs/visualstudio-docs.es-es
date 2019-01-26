---
title: Procedimiento Localizar una característica | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26eb3a1352228d48fb451e3a3520162cdea18b73
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867382"
---
# <a name="how-to-localize-a-feature"></a>Procedimiento Localizar una característica
  De forma predeterminada, las descripciones y títulos de las características utilizan los valores de cadena codificados de forma rígida. Para localizar el título de la característica y la descripción, reemplace las cadenas con expresiones que hacen referencia a los recursos localizados.  
  
## <a name="localize-a-feature"></a>Localizar una característica  
  
#### <a name="to-localize-a-feature"></a>Para localizar una característica  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **Feature1** nodo y, a continuación, elija **Agregar recurso de características**.  
  
2.  En el **Agregar recurso** diálogo cuadro, elija **todos los idiomas** en la lista según la referencia cultural para el archivo de recursos de características de lenguaje de forma predeterminada.  
  
3.  Repita el paso anterior para cada idioma localizado, elegir los idiomas de su elección para la característica localizada los archivos de recursos.  
  
     Se crean archivos de recursos de características independientes: uno para el idioma predeterminado y otro para cada idiomas localizados que desee admitir.  
  
4.  Abra cada archivo de recursos en el Editor de recursos y, a continuación, escriba todos los identificadores de cadena y sus valores.  
  
     Por ejemplo, en el archivo de recursos de característica predeterminado, escriba un identificador de cadena de **título** con un valor de **Mi título de la característica**, y un segundo identificador de cadena del **descripción** con un valor de **Mi descripción de la característica**. Para cada archivo de recursos localizado, use la misma cadena de identificadores utilizados en el recurso de la característica de forma predeterminada, pero especifique las cadenas localizadas para los valores.  
  
5.  Después de escribir todos los valores de recursos, abra el menú contextual de la característica (por ejemplo, *Feature1.feature*) y, a continuación, elija **Ver diseñador** para abrir la característica en el Diseñador de características.  
  
6.  Para localizar el **título** y **descripción** los campos de la característica, use el siguiente formato para especificar los valores en sus cuadros:  
  
     `$Resources:` *Identificador de cadena*  
  
     Por ejemplo, escriba $Resources:**título** en el **título de la característica** cuadro y $Resources:**descripción** en el **descripción de la característica** cuadro .  
  
     Los identificadores de cadena deben coincidir con los que se usan en los archivos de recursos.  
  
7.  Elija la **F5** clave para compilar y ejecutar la aplicación.  
  
8.  En SharePoint, abra el **acciones del sitio** menú, elija **configuración del sitio**y, a continuación, en el **acciones del sitio** sección elegir el **administrar las características del sitio** vínculo.  
  
9. En SharePoint, cambie el idioma de presentación predeterminado.  
  
     El título de la característica localizado y la descripción aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.  
  
## <a name="see-also"></a>Vea también
 [Localizar soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Cómo: Agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)   
 [Cómo: Localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Cómo: Localizar código](../sharepoint/how-to-localize-code.md)  
