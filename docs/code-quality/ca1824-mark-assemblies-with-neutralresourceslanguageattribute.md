---
title: 'CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: beaef23dd5b3047d1d65b90fdd984dfdedd7e145
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31916392"
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

El <xref:System.Resources.NeutralResourcesLanguageAttribute> atributo informa al administrador de recursos de referencia cultural predeterminada de una aplicación. Si los recursos de la referencia cultural de forma predeterminada se incrustan en el ensamblado principal de la aplicación, y <xref:System.Resources.ResourceManager> tiene que recuperar los recursos que pertenecen a la misma referencia cultural que la referencia cultural predeterminada, la <xref:System.Resources.ResourceManager> usa automáticamente los recursos ubicados en el ensamblado principal en lugar de buscar un ensamblado satélite. Esto omite el sondeo de ensamblado habitual, mejora el rendimiento de búsqueda para el primer recurso de carga y puede reducir el espacio de trabajo.

> [!TIP]
> Vea [empaquetar e implementar recursos](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) para el proceso que <xref:System.Resources.ResourceManager> usa para buscar archivos de recursos.

## <a name="fix-violations"></a>Corregir infracciones

Para corregir una infracción de esta regla, agregue el atributo al ensamblado y especificar el idioma de los recursos de la referencia cultural neutra.

### <a name="to-specify-the-neutral-language-for-resources"></a>Para especificar el idioma neutro para recursos

1. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, seleccione **propiedades**.

2. Seleccione el **aplicación** pestaña y, a continuación, seleccione **información de ensamblado**.

   > [!NOTE]
   > Si el proyecto es un proyecto de .NET estándar o .NET Core, seleccione la **paquete** ficha.

3. Seleccione el idioma de la **idioma neutro** o **idioma neutro de ensamblado** lista desplegable.

4. Seleccione **Aceptar**.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Está permitido para suprimir una advertencia de esta regla. Sin embargo, puede degradar el rendimiento de inicio.

## <a name="see-also"></a>Vea también

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Recursos en aplicaciones de escritorio (. NET)](/dotnet/framework/resources/)
- [CA1703: las cadenas de recursos deberían tener la ortografía correcta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701 - cadena de recurso deben mayúsculas y minúsculas en las palabras compuestas correctamente](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)