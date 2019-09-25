---
title: 'CA1824: Marcar los ensamblados con NeutralResourcesLanguageAttribute'
ms.date: 03/29/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df5c0db4e9e141e5833893bbbb447328eab8851e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233341"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: Marcar los ensamblados con NeutralResourcesLanguageAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|Identificador de comprobación|CA1824|
|Categoría|Microsoft.Performance|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Un ensamblado contiene un recurso basado en **resx**pero no tiene aplicado <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> el.

## <a name="rule-description"></a>Descripción de la regla

El <xref:System.Resources.NeutralResourcesLanguageAttribute> atributo informa al administrador de recursos de la referencia cultural predeterminada de una aplicación. Si los recursos de la referencia cultural predeterminada están incrustados en el ensamblado principal <xref:System.Resources.ResourceManager> de la aplicación y tiene que recuperar los recursos que pertenecen a la misma referencia cultural <xref:System.Resources.ResourceManager> que la referencia cultural predeterminada, usa automáticamente los recursos que se encuentran en el ensamblado principal. en lugar de buscar un ensamblado satélite. Esto omite el sondeo de ensamblado habitual, mejora el rendimiento de la búsqueda para el primer recurso que se carga y puede reducir el espacio de trabajo.

> [!TIP]
> Vea [empaquetar e implementar recursos](/dotnet/framework/resources/packaging-and-deploying-resources-in-desktop-apps) para el proceso que <xref:System.Resources.ResourceManager> utiliza para buscar archivos de recursos.

## <a name="fix-violations"></a>Corregir infracciones

Para corregir una infracción de esta regla, agregue el atributo al ensamblado y especifique el idioma de los recursos de la referencia cultural neutra.

### <a name="to-specify-the-neutral-language-for-resources"></a>Para especificar el idioma neutro para los recursos

1. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, seleccione **propiedades**.

2. Seleccione la pestaña **aplicación** y, a continuación, seleccione **información de ensamblado**.

   > [!NOTE]
   > Si el proyecto es un proyecto de .NET Standard o .NET Core, seleccione la pestaña **paquete** .

3. Seleccione el idioma en la lista desplegable Idioma **neutro** o **idioma neutro del ensamblado** .

4. Seleccione **Aceptar**.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Se permite suprimir una advertencia de esta regla. Sin embargo, el rendimiento de inicio puede degradarse.

## <a name="see-also"></a>Vea también

- <xref:System.Resources.NeutralResourcesLanguageAttribute>
- [Recursos en aplicaciones de escritorio (.NET)](/dotnet/framework/resources/)
- [CA1703: las cadenas de recursos deben estar escritas correctamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)
- [CA1701: las palabras compuestas de cadena de recurso deben tener mayúsculas y minúsculas](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)