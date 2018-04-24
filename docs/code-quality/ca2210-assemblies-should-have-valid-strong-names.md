---
title: 'CA2210: Los ensamblados deben tener nombres seguros válidos'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7421cee4e1b561d4efec7b843d12a7dcf5a67a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Los ensamblados deben tener nombres seguros válidos
|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|Identificador de comprobación|CA2210|
|Categoría|Microsoft.Design|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un ensamblado no está firmado con un nombre seguro, no se pudo comprobar el nombre seguro, o el nombre seguro no sería válido sin la configuración del registro actual del equipo.

## <a name="rule-description"></a>Descripción de la regla
 Esta regla recupera y comprueba el nombre seguro de un ensamblado. Se produce una infracción si se cumple alguna de las siguientes acciones:

-   El ensamblado no tiene un nombre seguro.

-   El ensamblado se modificó después de iniciar sesión.

-   El ensamblado tiene la firma retrasada.

-   El ensamblado se firmó incorrectamente o error en la firma.

-   El ensamblado requiere una configuración del registro pasar la comprobación. Por ejemplo, la herramienta de nombre seguro (Sn.exe) se utilizó para omitir la comprobación para el ensamblado.

 El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado. Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados. Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo. Un ensamblado sin un nombre seguro consta de las siguientes desventajas:

-   No se puede comprobar sus orígenes.

-   Common language runtime no puede advertir a los usuarios si se ha modificado el contenido del ensamblado.

-   No se puede cargar en la caché global de ensamblados.

 Tenga en cuenta que al cargar y analizar un ensamblado con firma retrasada, debe deshabilitar la comprobación para el ensamblado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 **Para crear un archivo de clave**

 Utilice uno de los siguientes procedimientos:

-   Use la herramienta Assembly Linker (Al.exe) proporcionada por el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.

-   Para el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v1.0 o v1.1, utilice uno los <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo.

-   Para el [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use la `/keyfile` o `/keycontainer` opción del compilador [/KEYFILE (especificar clave o par de claves para firmar un ensamblado)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [/KEYCONTAINER (especificar un contenedor de claves para firmar un ensamblado)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) opción del vinculador de C++).

 **Para firmar el ensamblado con un nombre seguro en Visual Studio**

1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra la solución.

2.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades.**

3.  Haga clic en el **firma** pestaña y seleccione la **firmar el ensamblado** casilla de verificación.

4.  De **elegir un archivo de clave de nombre seguro**, seleccione **nuevo**.

     El **crear clave de nombre seguro** se mostrará la ventana.

5.  En **nombre de archivo de clave**, escriba un nombre para la clave de nombre seguro.

6.  Elija si desea proteger la clave con una contraseña y, a continuación, haga clic en **Aceptar**.

7.  En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **generar**.

 **Para firmar el ensamblado con un nombre seguro fuera de Visual Studio**

-   Use la herramienta de nombre seguro (Sn.exe) proporcionada por el [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK. Para obtener más información, vea [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Sólo suprima las advertencias de esta regla si el ensamblado se usa en un entorno donde manipule el contenido no es un problema.

## <a name="see-also"></a>Vea también
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> [Cómo: firmar un ensamblado con un nombre seguro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name) [Sn.exe (herramienta de nombre seguro)](/dotnet/framework/tools/sn-exe-strong-name-tool)