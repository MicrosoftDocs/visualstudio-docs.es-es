---
title: 'CA2210: Los ensamblados deben tener nombres seguros válidos | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f94183c6051ed0c2603bbfe35484fabb83a2160f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697985"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Los ensamblados deben tener nombres seguros válidos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 **Para crear un archivo de clave**

 Use uno de los siguientes procedimientos:

- Use la herramienta Assembly Linker (Al.exe) proporcionada por el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Para el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 o v1.1, use el <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> atributo.

- Para el [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], use el `/keyfile` o `/keycontainer` opción del compilador [/keyfile (especificar clave o par de claves para firmar un ensamblado)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) o [/KEYCONTAINER (especificar un contenedor de claves para firmar un ensamblado)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) opción del vinculador de C++).

  **Para firmar el ensamblado con un nombre seguro en Visual Studio**

1. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], abra la solución.

2. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **propiedades.**

3. Haga clic en el **firma** pestaña y seleccione el **firmar el ensamblado** casilla de verificación.

4. Desde **elegir un archivo de clave de nombre seguro**, seleccione **New**.

    El **crear clave de nombre seguro** mostrará la ventana.

5. En **nombre de archivo de clave**, escriba un nombre para la clave de nombre seguro.

6. Elija si desea proteger la clave con una contraseña y, a continuación, haga clic en **Aceptar**.

7. En **el Explorador de soluciones**, haga clic en el proyecto y, a continuación, haga clic en **compilar**.

   **Para firmar el ensamblado con un nombre seguro fuera de Visual Studio**

- Utilice la herramienta de nombre seguro (Sn.exe) proporcionada por el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Para obtener más información, vea [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Sólo suprima una advertencia de esta regla si el ensamblado se usa en un entorno donde no es una preocupación manipule el contenido.

## <a name="see-also"></a>Vea también
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Cómo: Firmar un ensamblado con un nombre seguro](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (herramienta de nombre seguro)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
