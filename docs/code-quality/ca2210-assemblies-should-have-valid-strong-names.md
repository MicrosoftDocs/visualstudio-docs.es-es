---
title: 'CA2210: Los ensamblados deben tener nombres seguros válidos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89edba30a95d61268aebb26de8d973f6201c0fcf
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714754"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Los ensamblados deben tener nombres seguros válidos

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|Identificador de comprobación|CA2210|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Un ensamblado no está firmado con un nombre seguro, no se puede comprobar el nombre seguro o no es válida sin la configuración del registro actual del equipo.

## <a name="rule-description"></a>Descripción de la regla

Esta regla recupera y comprueba el nombre seguro de un ensamblado. Se produce una infracción si se cumple alguna de las siguientes acciones:

- El ensamblado no tiene un nombre seguro.

- El ensamblado se modificó después de iniciar sesión.

- El ensamblado está firmado con retraso.

- El ensamblado se firmó incorrectamente o no se pudo firmar.

- El ensamblado requiere la configuración del registro pasar la comprobación. Por ejemplo, la herramienta de nombre seguro (Sn.exe) se usó para omitir la comprobación del ensamblado.

El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado. Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados. Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo. Un ensamblado sin un nombre seguro tiene las siguientes desventajas:

- No se puede comprobar sus orígenes.

- Common language runtime no puede advertir a los usuarios si se han modificado el contenido del ensamblado.

- No se pueden cargar en la caché global de ensamblados.

Tenga en cuenta que para cargar y analizar un ensamblado con firma retrasada, debe deshabilitar la comprobación del ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

### <a name="create-a-key-file"></a>Crear un archivo de clave

Use uno de los siguientes procedimientos:

- Use la [herramienta Assembly Linker (Al.exe)](/dotnet/framework/tools/al-exe-assembly-linker).

- Para .NET Framework 2.0, usar el `/keyfile` o `/keycontainer` opción del compilador [/keyfile (especificar clave o par de claves para firmar un ensamblado)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [/KEYCONTAINER (especificar un contenedor de claves para firmar un ensamblado)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) opción del vinculador en C++).

- Para .NET Framework v1.0 o v1.1, use el <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo.

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Firmar el ensamblado con un nombre seguro en Visual Studio

1. En Visual Studio, abra la solución.

2. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades.**

3. Haga clic en el **firma** pestaña y seleccione el **firmar el ensamblado** casilla de verificación.

4. Desde **elegir un archivo de clave de nombre seguro**, seleccione **New**.

   El **crear clave de nombre seguro** mostrará la ventana.

5. En **nombre de archivo de clave**, escriba un nombre para la clave de nombre seguro.

6. Elija si desea proteger la clave con una contraseña y, a continuación, haga clic en **Aceptar**.

7. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **compilar**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Firmar el ensamblado con un nombre seguro fuera de Visual Studio

Use la [herramienta nombre seguro (Sn.exe)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Sólo suprima una advertencia de esta regla si el ensamblado se usa en un entorno donde no es una preocupación manipule el contenido.

## <a name="see-also"></a>Vea también

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Cómo: Firma de un ensamblado con un nombre seguro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (Herramienta de nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool)