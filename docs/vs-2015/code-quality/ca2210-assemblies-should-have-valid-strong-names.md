---
title: 'CA2210: los ensamblados deben tener nombres seguros válidos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548205"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Los ensamblados deben tener nombres seguros válidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|Identificador de comprobación|CA2210|
|Category|Microsoft. Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Un ensamblado no está firmado con un nombre seguro, no se pudo comprobar el nombre seguro o el nombre seguro no sería válido sin la configuración del registro actual del equipo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla recupera y comprueba el nombre seguro de un ensamblado. Se produce una infracción si se cumple alguna de las siguientes condiciones:

- El ensamblado no tiene un nombre seguro.

- El ensamblado se modificó después de la firma.

- El ensamblado tiene firma retrasada.

- El ensamblado se firmó incorrectamente o no se pudo firmar.

- El ensamblado requiere la configuración del registro para pasar la comprobación. Por ejemplo, la herramienta de nombre seguro (Sn.exe) se utilizó para omitir la comprobación del ensamblado.

  El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado. Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados. Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo. Un ensamblado sin nombre seguro tiene los siguientes inconvenientes:

- No se pueden comprobar sus orígenes.

- El Common Language Runtime no puede advertir a los usuarios si se ha modificado el contenido del ensamblado.

- No se puede cargar en la caché global de ensamblados.

  Tenga en cuenta que para cargar y analizar un ensamblado con firma retrasada, debe deshabilitar la comprobación para el ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 **Para crear un archivo de clave**

 Realice uno de los siguientes procedimientos:

- Use la herramienta Assembly Linker (Al.exe) proporcionada por el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Para [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v 1.0 o v 1.1, use el <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo o.

- Para [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , use las opciones del `/keyfile` `/keycontainer` compilador o [/keyfile (especificar la clave o el par de claves para firmar un ensamblado)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) o [/keycontainer (especificar un contenedor de claves para firmar un ensamblado)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) opción del enlazador en C++).

  **Para firmar el ensamblado con un nombre seguro en Visual Studio**

1. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , abra la solución.

2. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **propiedades.**

3. Haga clic en la pestaña **firma** y active la casilla **firmar el ensamblado** .

4. En **Elija un archivo de clave de nombre seguro**, seleccione **nuevo**.

    Se mostrará la ventana **crear clave de nombre seguro** .

5. En **nombre de archivo de clave**, escriba un nombre para la clave de nombre seguro.

6. Elija si desea proteger la clave con una contraseña y, a continuación, haga clic en **Aceptar**.

7. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto y, a continuación, haga clic en **compilar**.

   **Para firmar el ensamblado con un nombre seguro fuera de Visual Studio**

- Use la herramienta de nombre seguro (Sn.exe) proporcionada por el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Para obtener más información, vea [Sn.exe (herramienta de nombre seguro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima solo una advertencia de esta regla si el ensamblado se usa en un entorno en el que la alteración del contenido no es un problema.

## <a name="see-also"></a>Consulte también
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Cómo: firmar un ensamblado con un nombre seguro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (herramienta de nombre seguro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
