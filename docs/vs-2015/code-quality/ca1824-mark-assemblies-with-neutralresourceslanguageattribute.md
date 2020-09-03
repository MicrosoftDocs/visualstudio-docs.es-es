---
title: 'CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545293"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marcar los ensamblados con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|Identificador de comprobación|CA1824|
|Category|Microsoft. performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un ensamblado contiene un recurso basado en **resx**pero no tiene <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado el.

## <a name="rule-description"></a>Descripción de la regla
 El atributo **NeutralResourcesLanguage** informa a **ResourceManager** del idioma que se usó para mostrar los recursos de la referencia cultural neutra de un ensamblado. Cuando busca recursos en la misma referencia cultural que el idioma de los recursos neutros, **ResourceManager** usa automáticamente los recursos que se encuentran en el ensamblado principal. Lo hace en lugar de buscar un ensamblado satélite que tenga la referencia cultural de la interfaz de usuario actual para el subproceso actual. Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo.

## <a name="fixing-violations"></a>Corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado y especifique el idioma de los recursos de la referencia cultural neutra.

## <a name="specifying-the-language"></a>Especificar el idioma

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Para especificar el idioma del recurso de la referencia cultural neutra

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades**.

2. En la barra de navegación izquierda, seleccione **aplicación**y, a continuación, haga clic en **información de ensamblado**.

3. En el cuadro de diálogo **información de ensamblado** , seleccione el idioma en la lista desplegable **idioma neutro** .

4. Haga clic en **Aceptar**.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Se permite suprimir una advertencia de esta regla. Sin embargo, el rendimiento de inicio puede disminuir.
