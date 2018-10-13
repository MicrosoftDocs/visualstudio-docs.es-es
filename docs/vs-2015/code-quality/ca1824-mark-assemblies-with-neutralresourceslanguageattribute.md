---
title: 'CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 20bfe8456e6047192f15f4473df5366fd0d9fba1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49275150"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|Identificador de comprobación|CA1824|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un ensamblado contiene un **ResX**-recurso basado en pero no tiene el <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado a él.

## <a name="rule-description"></a>Descripción de la regla
 El **NeutralResourcesLanguage** atributo informa a la **ResourceManager** del lenguaje que se usó para mostrar los recursos de la referencia cultural neutra para un ensamblado. Cuando busca recursos en la misma referencia cultural que el idioma de los recursos neutros el **ResourceManager** usa automáticamente los recursos que se encuentran en el ensamblado principal. Para ello, en lugar de buscar un ensamblado satélite que tiene la referencia cultural actual interfaz de usuario para el subproceso actual. Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo.

## <a name="fixing-violations"></a>Corregir las infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado y especificar el idioma de los recursos de la referencia cultural neutra.

## <a name="specifying-the-language"></a>Especifica el lenguaje

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Para especificar el idioma del recurso de la referencia cultural neutra

1.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades**.

2.  En la barra de navegación izquierdo, seleccione **aplicación**y, a continuación, haga clic en **información de ensamblado**.

3.  En el **información de ensamblado** diálogo cuadro, seleccione el idioma de la **idioma neutro** lista desplegable.

4.  Haga clic en **Aceptar**.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es admisible para suprimir una advertencia de esta regla. Sin embargo, podría disminuir el rendimiento de inicio.



