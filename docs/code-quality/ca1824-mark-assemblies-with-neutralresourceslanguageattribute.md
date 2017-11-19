---
title: 'CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c1d2138065946bfd14abfedbbffdd2dc5b433d89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|Identificador de comprobación|CA1824|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un ensamblado contiene un **ResX**-recurso basado en pero no tiene la <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado.  
  
## <a name="rule-description"></a>Descripción de la regla  
 El **NeutralResourcesLanguage** atributo informa a la **ResourceManager** del lenguaje que se usa para mostrar los recursos de la referencia cultural neutral de un ensamblado. Cuando busca recursos en la misma referencia cultural que el idioma de recursos neutrales, el **ResourceManager** usa automáticamente los recursos que se encuentran en el ensamblado principal. Esto consigue en lugar de buscar un ensamblado satélite con la referencia cultural actual interfaz de usuario para el subproceso actual. Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo.  
  
## <a name="fixing-violations"></a>Corregir infracciones  
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado y especificar el idioma de los recursos de la referencia cultural neutra.  
  
## <a name="specifying-the-language"></a>Especificación del idioma  
  
#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Para especificar el idioma del recurso de la referencia cultural neutra  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.  
  
2.  En la barra de navegación izquierdo, seleccione **aplicación**y, a continuación, haga clic en **información de ensamblado**.  
  
3.  En el **información de ensamblado** diálogo cuadro, seleccione el idioma de la **idioma neutro** lista desplegable.  
  
4.  Haga clic en **Aceptar**.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Está permitido para suprimir una advertencia de esta regla. Sin embargo, puede reducir el rendimiento de inicio.