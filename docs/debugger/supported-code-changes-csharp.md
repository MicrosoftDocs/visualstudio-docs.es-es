---
title: Admite los cambios de código (C# y Visual Basic) | Microsoft Docs
ms.date: 10/11/2017
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 865b5c220a410c9b0d744263820a50dd1bb9395a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878632"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Cambios admitidos en el código (C# y Visual Basic)
Editar y continuar controla la mayoría de los tipos de cambios de código dentro de los cuerpos de método. Ahora bien, durante la depuración, no es posible efectuar la mayoría de cambios fuera de los cuerpos de método y algunos cambios dentro de estos. Para efectuar dichos cambios no compatibles, es necesario detener la depuración y reiniciar con una versión nueva del código.

## <a name="supported-changes-to-code"></a>Cambios admitidos en código

En la tabla siguiente muestra los cambios que pueden realizarse en código C# y Visual Basic durante una sesión de depuración sin tener que reiniciar la sesión.

|Elemento o característica del lenguaje|Operación de edición admitidas|Limitaciones|
|-|-|-|
|Tipos|Agregue los métodos, campos, constructores, et al.|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Agregar o modificar|No|
|expresiones de Async y await|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objetos dinámicos|Agregar o modificar|No|
|expresiones lambda|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expresiones de LINQ|Agregar o modificar|[Igual que las expresiones lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Nuevas características de lenguaje como la interpolación de cadena y operadores condicionales null generalmente son compatibles con Editar y continuar. Para obtener la información más reciente, consulte el [admite edita Enc](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) página.

## <a name="unsupported-changes-to-code"></a>Cambios no admitidos en código
 Los siguientes cambios no se puede aplicar al código de C# y Visual Basic durante una sesión de depuración:  
  
-   Cambios en la instrucción actual o en cualquier otra instrucción activa.  
  
     Entre las instrucciones activas se incluye cualquier instrucción, en funciones de la pila de llamadas, que haya sido llamada para llegar a la instrucción actual.  
  
     Un fondo amarillo marca la instrucción actual en la ventana de código fuente. Un fondo sombreado marca otras instrucciones activas; son de solo lectura. Estos colores predeterminados se pueden cambiar en el cuadro de diálogo **Opciones**.

- La siguiente tabla muestra los cambios no admitidos en código mediante el elemento de lenguaje.

|Elemento o característica del lenguaje|Operación de edición no admitida|
|-|-|
|Todos los elementos de código|Cambiar nombre|
|Espacios de nombres|Add|
|Espacios de nombres, tipos, miembros|Eliminar|
|Genéricos|Agregar o modificar|
|Interfaces|Modificar|
|Tipos|Agregar miembro abstracto o virtual, agregue invalidación (vea [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipos|Agregar destructor|
|Miembros|Modificar a un miembro que hacen referencia a un tipo de interoperabilidad incrustado|
|Miembros (Visual Basic)|Modificar a un miembro con la instrucción On Error o Resume|
|Miembros (Visual Basic)|Modificar a un miembro que contiene una cláusula de consulta de agregado, Group By, Join Simple o LINQ de unirse a grupo|
|Métodos|Modificar las firmas|
|Métodos|Asegúrese de un método abstracto se convierten en no abstracta mediante la adición de un cuerpo de método|
|Métodos|Eliminar el cuerpo del método|
|Atributos|Agregar o modificar|
|Eventos o propiedades|Modificar un parámetro de tipo, el tipo base, tipo de delegado o tipo de valor devuelto |
|Los operadores o indizadores|Modificar un parámetro de tipo, el tipo base, tipo de delegado o tipo de valor devuelto |
|bloques catch|Modificar cuando contiene una instrucción activa|
|bloques try-catch-finally|Modificar cuando contiene una instrucción activa|
|Using (instrucciones)|Add|
|métodos o lambdas asincrónicas|Modificar un método o función lambda asincrónica en un proyecto destinado a .NET Framework 4 y reducir (consulte [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificar un iterador en un proyecto destinado a .NET Framework 4 y reducir (consulte [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
  
## <a name="unsafe-code"></a>Código no seguro  
 Los cambios en el código no seguro tienen las mismas limitaciones que los cambios en el código seguro, con una restricción adicional: Editar y continuar no admite cambios en el código no seguro que esté dentro de un método que contiene el `stackalloc` operador.  

## <a name="unsupported-app-scenarios"></a>Escenarios de aplicaciones no compatibles

Plataformas y aplicaciones no compatibles se incluyen ASP.NET 5, 5 de Silverlight y Windows 8.1.

> [!NOTE]
> Las aplicaciones que son compatibles incluyen UWP en x86 y x64 aplicaciones que tienen como destino .NET Framework 4.6 y Windows 10 escritorio o versiones posteriores (.NET Framework es una versión de escritorio).
  
## <a name="unsupported-scenarios"></a>Escenarios no admitidos  
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:  
  
-   Depuración en modo mixto (nativa o administrada).  
  
-   Depuración de SQL.  
  
-   Depuración de un volcado de Dr. Volcado de memoria de Watson.  
  
-   Depuración de una aplicación incrustada en tiempo de ejecución.  
  
-   Depurar una aplicación utilizando asociar al proceso (**Depurar > asociar al proceso**) en lugar de ejecutar la aplicación eligiendo **iniciar** desde el **depurar** menú.  
  
-   Depuración de código optimizado.  
  
-   Depurar una versión anterior del código cuando no ha sido posible generar una nueva versión debido a errores de compilación.
  
## <a name="see-also"></a>Vea también  
 [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)   
 [Cómo: Uso de Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)