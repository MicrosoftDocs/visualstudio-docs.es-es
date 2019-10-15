---
title: Opciones de configuración del analizador de FxCop
ms.date: 09/23/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ae16a0fd101005f0bc81a3f5f204f5e774976ebb
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305844"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Opciones de ámbito de reglas para los analizadores de FxCop

Algunas reglas del analizador de FxCop permiten restringir qué partes del código base deben aplicarse. En esta página se enumeran las opciones de configuración de ámbito disponibles, sus valores permitidos y las reglas a las que se pueden aplicar. Para usar estas opciones, debe especificarlas en un [archivo EditorConfig](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project).

Estas opciones de configuración están disponibles a partir de la versión 2.6.3 del paquete NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) .

> [!TIP]
> Para ver la lista completa de las opciones disponibles para una versión determinada del paquete FxCopAnalyzers, examine el archivo Configuration.md del *analizador* en la carpeta de *documentación* del paquete. El archivo se encuentra en *% userprofile% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-2 @ no__t-3version @ no__t-4\documentation\Analyzer Configuration.MD*. Este archivo de documentación de configuración se incluye con cada versión del paquete, a partir de la versión 2.6.5. Este es un ejemplo de cómo se documenta una opción en el archivo *Configuration.MD del analizador* :
>
> Nombre de opción: `sufficient_IterationCount_for_weak_KDF_algorithm` @ no__t-1
> Valores de opción: valores enteros \
> Valor predeterminado: Específico de cada regla configurable (' 100000 ' de forma predeterminada para la mayoría de las reglas) \
> Ejemplo: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Qué parte de la superficie de API se va a analizar | `public`<br/>`internal` o `friend`<br/>`private`<br/>`all`<br/><br/>Separar varios valores con una coma (,) | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217-do-not-mark-enums-with-flagsattribute.md)<br/>[CA2225](ca2225-operator-overloads-have-named-alternates.md)<br/>[CA2226](ca2226-operators-should-have-symmetrical-overloads.md)<br/>[CA2231](ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)<br/>[CA2234](ca2234-pass-system-uri-objects-instead-of-strings.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Si se omiten los métodos asincrónicos que no devuelven un valor | `true`<br/>`false` | `false` | [CA2007](ca2007-do-not-directly-await-task.md) |

> [!NOTE]
> En la versión 2.6.3 y versiones anteriores del paquete de analizador, esta opción se denominaba `skip_async_void_methods`.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Si se van a excluir de la regla [los parámetros de tipo](/dotnet/csharp/programming-guide/generics/generic-type-parameters) de un solo carácter, por ejemplo, `S` en `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> En la versión 2.6.3 y versiones anteriores del paquete de analizador, esta opción se denominaba `allow_single_letter_type_parameters`.

## <a name="output_kind"></a>output_kind

| Descripción | Valores permitidos | Valor predeterminado | Reglas configurables |
| - | - | - | - |
| Especifica que debe analizarse el código de un proyecto que genera este tipo de ensamblado. | Uno o más campos de la enumeración <xref:Microsoft.CodeAnalysis.OutputKind><br/><br/>Separar varios valores con una coma (,) | Todos los tipos de salida | [CA2007](ca2007-do-not-directly-await-task.md) |