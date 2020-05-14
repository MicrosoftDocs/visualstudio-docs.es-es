---
title: Cambios de código admitidos (C# y Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44881035da14483c3ddf1f4c48cb3957a1ce8b50
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729086"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Cambios de código admitidos (C# y Visual Basic)
Editar y continuar controla la mayoría de los tipos de cambios de código dentro de los cuerpos de método. Ahora bien, durante la depuración, no es posible efectuar la mayoría de cambios fuera de los cuerpos de método y algunos cambios dentro de estos. Para efectuar dichos cambios no compatibles, es necesario detener la depuración y reiniciar con una versión nueva del código.

## <a name="supported-changes-to-code"></a>Cambios admitidos en el código

En la tabla siguiente se muestran los cambios que se pueden realizar en el código de C# y Visual Basic durante una sesión de depuración sin reiniciar la sesión.

|Elemento o característica del lenguaje|Operación de edición admitida|Limitaciones|
|-|-|-|
|Tipos|Agregar métodos, campos, constructores y otros|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Agregar o modificar|No|
|Expresiones async/await|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objetos dinámicos|Agregar o modificar|No|
|expresiones lambda|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expresiones LINQ|Agregar o modificar|[Igual que las expresiones lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Las características de lenguaje más recientes, como la interpolación de cadenas y los operadores condicionales NULL, se admiten generalmente mediante Editar y continuar. Para obtener la información más reciente, consulte la página [Ediciones admitidas en Editar y continuar](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits).

## <a name="unsupported-changes-to-code"></a>Cambios no admitidos en el código
 Los siguientes cambios no se pueden aplicar al código de C# y Visual Basic durante una sesión de depuración:

- Cambios en la instrucción actual o en cualquier otra instrucción activa.

     Entre las instrucciones activas se incluye cualquier instrucción, en funciones de la pila de llamadas, que haya sido llamada para llegar a la instrucción actual.

     Un fondo amarillo marca la instrucción actual en la ventana de código fuente. Un fondo sombreado marca otras instrucciones activas; son de solo lectura. Estos colores predeterminados se pueden cambiar en el cuadro de diálogo **Opciones**.

- En la tabla siguiente se muestran los cambios no admitidos en el código mediante el elemento de lenguaje.

|Elemento o característica del lenguaje|Operación de edición no admitida|
|-|-|
|Todos los elementos de código|Cambiar nombre|
|Espacios de nombres|Agregar|
|Espacios de nombres, tipos, miembros|Eliminar|
|Genéricos|Agregar o modificar|
|Interfaces|Modificar|
|Tipos|Agregar miembro abstracto o virtual, agregar invalidación (vea los [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipos|Agregar destructor|
|Miembros|Modificar un miembro que hace referencia a un tipo de interoperabilidad incrustado|
|Miembros|Modificar un miembro estático una vez que ya se ha accedido mediante la ejecución de código|
|Miembros (Visual Basic)|Modificar un miembro con la instrucción Al ocurrir un error o Reanudar|
|Miembros (Visual Basic)|Modificar un miembro que contenga una cláusula de consulta de LINQ Aggregate, Group By, Simple Join o Group Join|
|Métodos|Modificar firmas|
|Métodos|Convertir un método abstracto en no abstracto agregando un cuerpo del método|
|Métodos|Eliminar cuerpo del método|
|Atributos|Agregar o modificar|
|Eventos o propiedades|Modificar un parámetro de tipo, tipo base, tipo de delegado o tipo de valor devuelto |
|Operadores o indizadores|Modificar un parámetro de tipo, tipo base, tipo de delegado o tipo de valor devuelto |
|bloques catch|Modificar cuando contiene una instrucción activa|
|Bloques try-catch-finally|Modificar cuando contiene una instrucción activa|
|Using (instrucciones)|Agregar|
|Expresiones lambda/métodos asincrónicos|Modificar una expresión lambda o un método asincrónico en un proyecto destinado a .NET Framework 4 y versiones anteriores (vea los [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificar un iterador en un proyecto destinado a .NET Framework 4 y versiones anteriores (vea los [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Código no seguro
 Los cambios en el código no seguro tienen las mismas limitaciones que los cambios en el código seguro, con una restricción adicional: Editar y continuar no admite cambios en el código no seguro que esté incluido en un método que contiene el operador `stackalloc`.

## <a name="unsupported-app-scenarios"></a>Escenarios de aplicaciones no admitidas

Las aplicaciones y plataformas no admitidas incluyen ASP.NET 5, Silverlight 5 y Windows 8.1.

> [!NOTE]
> Entre las aplicaciones que se admiten se incluyen UWP en Windows 10 y aplicaciones x86 y x64 que tienen como destino el escritorio de .NET Framework 4.6 o versiones posteriores (.NET Framework es solo una versión de escritorio).

## <a name="unsupported-scenarios"></a>Escenarios no admitidos
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:

- Depuración en modo mixto (nativa o administrada).

- Depuración de SQL.

- Depuración de un volcado de Dr. Watson.

- Depuración de una aplicación incrustada en tiempo de ejecución.

- Depuración de una aplicación mediante la asociación al proceso (**Depurar > Asociar al proceso**) en lugar de ejecutar la aplicación al elegir **Inicio** en el menú **Depurar**.

- Depuración de código optimizado.

- Depurar una versión anterior del código cuando no ha sido posible generar una nueva versión debido a errores de compilación.

## <a name="see-also"></a>Vea también
- [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Cómo: Uso de Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)