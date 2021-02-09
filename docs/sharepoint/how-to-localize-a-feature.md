---
title: 'Cómo: localizar una característica | Microsoft Docs'
description: Aprenda a localizar títulos de características y descripciones en SharePoint reemplazando los valores de cadena codificados de forma rígida por expresiones que hacen referencia a recursos localizados.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4a3c427f207f6aac9f6a827eb6c24b799d635b46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913599"
---
# <a name="how-to-localize-a-feature"></a>Cómo: para localizar una característica
  De forma predeterminada, los títulos y las descripciones de las características usan valores de cadena codificados de forma rígida. Para localizar el título y la descripción de la característica, reemplace las cadenas por expresiones que hagan referencia a recursos localizados.

## <a name="localize-a-feature"></a>Localizar una característica

#### <a name="to-localize-a-feature"></a>Para localizar una característica

1. En **Explorador de soluciones**, abra el menú contextual del nodo **Feature1** y, a continuación, elija **Agregar recurso de característica**.

2. En el cuadro de diálogo **Agregar recurso** , elija **idioma invariable** de la lista como referencia cultural para el archivo de recursos de características de idioma predeterminado.

3. Repita el paso anterior para cada idioma localizado y elija los idiomas de su elección para los archivos de recursos de características localizados.

     Se crean archivos de recursos de características independientes: uno para el idioma predeterminado y otro para cada idioma localizado que desee admitir.

4. Abra cada archivo de recursos en el editor de recursos y, a continuación, escriba todos los identificadores de cadena y sus valores.

     Por ejemplo, en el archivo de recursos de características predeterminado, escriba un identificador de cadena de **título** con un valor de **mi título de característica** y un segundo identificador de cadena de **Descripción** con un valor de **mi Descripción de la característica**. Para cada archivo de recursos localizado, use los mismos identificadores de cadena que se usan en el recurso de característica predeterminado, pero especifique cadenas localizadas para los valores.

5. Después de especificar todos los valores de recursos, abra el menú contextual de la característica (por ejemplo, *Feature1. Feature*) y, a continuación, elija **Diseñador de vistas** para abrir la característica en el diseñador de características.

6. Para localizar los campos de **título** y **Descripción** en la característica, use el formato siguiente para escribir los valores en los cuadros:

     `$Resources:` *Identificador de cadena*

     Por ejemplo, escriba $Resources:**título** en el cuadro título de la **característica** y $Resources:**Descripción** en el cuadro Descripción de la **característica** .

     Los identificadores de cadena deben coincidir con los que se usan en los archivos de recursos.

7. Elija la tecla **F5** para compilar y ejecutar la aplicación.

8. En SharePoint, abra el menú **acciones del sitio** , elija Configuración del **sitio** y, a continuación, en la sección **acciones del sitio** , elija el vínculo **administrar las características del sitio** .

9. En SharePoint, cambie el idioma de presentación predeterminado.

     El título y la descripción de la característica localizada aparecen en la aplicación. Para mostrar los recursos localizados, el servidor de SharePoint debe tener instalado el paquete de idioma que coincide con la referencia cultural del archivo de recursos.

## <a name="see-also"></a>Vea también
- [Localización de soluciones de SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Cómo: para agregar un archivo de recursos](../sharepoint/how-to-add-a-resource-file.md)
- [Cómo: para localizar el marcado ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Cómo: para localizar código](../sharepoint/how-to-localize-code.md)
