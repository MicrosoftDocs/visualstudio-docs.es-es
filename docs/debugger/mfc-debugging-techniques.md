---
title: Técnicas de depuración de MFC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f2cd5345de8dfe62e56722a8e36713c6062b3cb
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693032"
---
# <a name="mfc-debugging-techniques"></a>Técnicas de depuración de MFC
Si está depurando un programa MFC, estas técnicas de depuración pueden resultar de utilidad.

## <a name="BKMK_In_this_topic"></a> En este tema
[AfxDebugBreak](#BKMK_AfxDebugBreak)

[La macro TRACE](#BKMK_The_TRACE_macro)

[Detectar pérdidas de memoria en MFC](#BKMK_Memory_leak_detection_in_MFC)

- [Realizar un seguimiento de las asignaciones de memoria](#BKMK_Tracking_memory_allocations)

- [Habilitar diagnósticos de memoria](#BKMK_Enabling_memory_diagnostics)

- [Tomar instantáneas de la memoria](#BKMK_Taking_memory_snapshots)

- [Ver estadísticas de memoria](#BKMK_Viewing_memory_statistics)

- [Realizar volcados de memoria de objetos](#BKMK_Taking_object_dumps)

  - [Interpretar volcados de memoria](#BKMK_Interpreting_memory_dumps)

  - [Personalizar volcados de memoria de objetos](#BKMK_Customizing_object_dumps)

  - [Reducir el tamaño de una configuración de compilación de MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)

  - [Compilar una aplicación MFC con la información de depuración para los módulos seleccionados](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)

## <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak
MFC proporciona una función especial, [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) , para incluir puntos de interrupción en el código fuente:

```cpp
AfxDebugBreak( );
```

En plataformas Intel, `AfxDebugBreak` produce el siguiente código, que se introduce en el código fuente en vez de en el código de kernel:

```cpp
_asm int 3
```

En otras plataformas, `AfxDebugBreak` simplemente llama a `DebugBreak`.

Asegúrese de quitar las instrucciones `AfxDebugBreak` cuando genere una versión de lanzamiento, o bien utilice `#ifdef _DEBUG` para encerrarlas.

[En este tema](#BKMK_In_this_topic)

## <a name="BKMK_The_TRACE_macro"></a> La macro TRACE
Para mostrar mensajes desde el programa en la [Ventana de salida](../ide/reference/output-window.md)del depurador, se puede utilizar la macro [ATLTRACE](https://msdn.microsoft.com/Library/c796baa5-e2b9-4814-a27d-d800590b102e) o la macro [TRACE](https://msdn.microsoft.com/Library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) de MFC. Al igual que las [aserciones](../debugger/c-cpp-assertions.md), las macros de seguimiento sólo están activas en la versión de depuración del programa y desaparecen al compilarse en la versión de lanzamiento.

Los siguientes ejemplos muestran algunas de las formas en las que se puede utilizar la macro **TRACE** . Al igual que `printf`, la macro **TRACE** puede utilizar varios argumentos.

```cpp
int x = 1;
int y = 16;
float z = 32.0;
TRACE( "This is a TRACE statement\n" );

TRACE( "The value of x is %d\n", x );

TRACE( "x = %d and y = %d\n", x, y );

TRACE( "x = %d and y = %x and z = %f\n", x, y, z );
```

La macro TRACE controla correctamente ambos char\* y wchar_t\* parámetros. En los ejemplos siguientes se muestra el uso de la macro TRACE junto con diferentes tipos de parámetros de cadena.

```cpp
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);

TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);

TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);
```

Para obtener más información sobre la macro **TRACE** , vea [Servicios de diagnóstico](/cpp/mfc/reference/diagnostic-services).

[En este tema](#BKMK_In_this_topic)

## <a name="BKMK_Memory_leak_detection_in_MFC"></a> Detectar pérdidas de memoria en MFC
MFC proporciona clases y funciones para detectar memoria asignada que no se desasigna nunca.

### <a name="BKMK_Tracking_memory_allocations"></a> Realizar un seguimiento de las asignaciones de memoria
En MFC, se puede utilizar la macro [DEBUG_NEW](https://msdn.microsoft.com/Library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) en lugar del operador **new** para ayudar a localizar pérdidas de memoria. En la versión de depuración del programa, `DEBUG_NEW` registra el nombre de archivo y número de línea para cada objeto que asigna. Cuando se compila una versión de lanzamiento de programa, `DEBUG_NEW` se resuelve como una simple operación **new** sin la información de nombre de archivo y número de línea. De este modo, el rendimiento de la versión de lanzamiento no disminuye.

Si no desea volver a escribir todo el programa para utilizar `DEBUG_NEW` en lugar de **new**, puede definir esta macro en los archivos de código fuente:

```cpp
#define new DEBUG_NEW
```

Cuando se realiza un [volcado de memoria de objetos](#BKMK_Taking_object_dumps), cada objeto asignado con `DEBUG_NEW` muestra el archivo y el número de línea donde fue asignado, lo que permite localizar con exactitud el origen de las pérdidas de memoria.

La versión de depuración del marco de trabajo de MFC utiliza `DEBUG_NEW` automáticamente, pero el código no lo hace. Si desea sacar partido de `DEBUG_NEW`, debe usar `DEBUG_NEW` de forma explícita, o bien usar la instrucción **#define new** como se indicó anteriormente.

[En este tema](#BKMK_In_this_topic)

### <a name="BKMK_Enabling_memory_diagnostics"></a> Habilitar diagnósticos de memoria
Para poder utilizar los servicios de diagnóstico de memoria, se debe habilitar la traza con diagnósticos.

**Para habilitar o deshabilitar los diagnósticos de memoria**

- Llame a la función global [AfxEnableMemoryTracking](https://msdn.microsoft.com/Library/0a40e0c4-855d-46e2-9577-a8f2346f47db) para habilitar o deshabilitar el asignador de memoria para diagnósticos. Como los diagnósticos de memoria se encuentran, de forma predeterminada, en la biblioteca de depuración, se utilizará normalmente esta función para desactivarlos temporalmente, lo cual incrementa la velocidad de ejecución del programa y reduce los resultados de diagnóstico.

  **Para seleccionar características específicas de diagnóstico de memoria con afxMemDF**

- Si desea un control más preciso sobre las características de diagnóstico de memoria, puede activar y desactivar selectivamente características individuales configurando el valor de la variable global de MFC [afxMemDF](https://msdn.microsoft.com/Library/cf117501-5446-4fce-81b3-f7194bc95086). Esta variable puede tener los siguientes valores, según especifica el tipo enumerado **afxMemDF**.

  |Valor|Descripción|
  |-----------|-----------------|
  |**allocMemDF**|Activa el asignador de memoria para diagnósticos (opción predeterminada).|
  |**delayFreeMemDF**|Retarda la liberación de memoria al llamar a `delete` o `free` hasta que termina el programa. Esto hace que el programa asigne la máxima cantidad posible de memoria.|
  |**checkAlwaysMemDF**|Llama a [AfxCheckMemory](/cpp/mfc/reference/diagnostic-services#afxcheckmemory) cada vez que se asigna o se libera memoria.|

  Estos valores se pueden utilizar combinados mediante una operación de disyunción lógica (OR), como se indica a continuación:

  ```C++
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;
  ```

  [En este tema](#BKMK_In_this_topic)

### <a name="BKMK_Taking_memory_snapshots"></a> Tomar instantáneas de la memoria

1. Cree un objeto [CMemoryState](/previous-versions/visualstudio/visual-studio-2010/2ads32e2(v=vs.100)) y llame a la función miembro [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint) . Esto crea la primera instantánea de memoria.

2. Después de que el programa realiza sus operaciones de asignación y desasignación de memoria, cree otro objeto `CMemoryState` y llame a `Checkpoint` para ese objeto. Esto hace que se tome una segunda instantánea del uso de memoria.

3. Cree un tercer objeto `CMemoryState` , llame a su función miembro [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) y proporcione como argumentos los dos objetos `CMemoryState` anteriores. Si existen diferencias entre los dos estados de memoria, la función `Difference` devuelve un valor distinto de cero. Esto indica que algunos bloques de memoria no se han desasignado.

    Este ejemplo muestra el aspecto del código:

    ```cpp
    // Declare the variables needed
    #ifdef _DEBUG
        CMemoryState oldMemState, newMemState, diffMemState;
        oldMemState.Checkpoint();
    #endif

        // Do your memory allocations and deallocations.
        CString s("This is a frame variable");
        // The next object is a heap object.
        CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );

    #ifdef _DEBUG
        newMemState.Checkpoint();
        if( diffMemState.Difference( oldMemState, newMemState ) )
        {
            TRACE( "Memory leaked!\n" );
        }
    #endif
    ```

    Tenga en cuenta que las instrucciones de comprobación de memoria están enmarcadas por **#ifdef _DEBUG / #endif** bloquea para que solo se compilan en versiones de depuración del programa.

    Ahora que ha detectado una pérdida de memoria, puede usar otra función miembro [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) , que le ayudará a buscarla.

    [En este tema](#BKMK_In_this_topic)

### <a name="BKMK_Viewing_memory_statistics"></a> Ver estadísticas de memoria
La función [CMemoryState::Difference](/cpp/mfc/reference/cmemorystate-structure#difference) examina dos objetos de estado de memoria y detecta cualquier objeto no desasignado del montón entre los estados inicial y final. Después de tomar instantáneas de la memoria y compararlas mediante `CMemoryState::Difference`, puede llamar a [CMemoryState::DumpStatistics](/cpp/mfc/reference/cmemorystate-structure#dumpstatistics) para obtener información sobre los objetos que no se han desasignado.

Considere el ejemplo siguiente:

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpStatistics();
}
```

Un volcado de memoria de ejemplo tiene el siguiente aspecto:

```cpp
0 bytes in 0 Free Blocks
22 bytes in 1 Object Blocks
45 bytes in 4 Non-Object Blocks
Largest number used: 67 bytes
Total allocations: 67 bytes
```

Los bloques libres son bloques cuya desasignación se retrasa si `afxMemDF` se configuró con el valor `delayFreeMemDF`.

Los bloques de objetos ordinarios, que se muestran en la segunda línea, permanecen asignados en el montón.

Entre los bloques que no son objetos se incluyen las matrices y las estructuras cuya memoria se asigna con `new`. En este caso, se asignó memoria en el montón para cuatro bloques que no son objetos, pero esa memoria no se desasignó.

`Largest number used` proporciona la memoria máxima utilizada por el programa en cualquier instante.

`Total allocations` proporciona la cantidad total de memoria utilizada por el programa.

[En este tema](#BKMK_In_this_topic)

### <a name="BKMK_Taking_object_dumps"></a> Realizar volcados de memoria de objetos
En un programa MFC, puede usar [CMemoryState:: DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) para volcar una descripción de todos los objetos del montón que no se han desasignado. `DumpAllObjectsSince` vuelca todos los objetos asignados desde el último [CMemoryState::Checkpoint](/cpp/mfc/reference/cmemorystate-structure#checkpoint). Si no se realizó ninguna llamada a `Checkpoint` , `DumpAllObjectsSince` produce un volcado de memoria de todos los objetos y elementos que no sean objetos actualmente en memoria.

> [!NOTE]
> Para poder utilizar el volcado de objetos MFC, debe [habilitar el seguimiento de diagnóstico](#BKMK_Enabling_memory_diagnostics).

> [!NOTE]
> MFC produce automáticamente un volcado de memoria de todos los objetos no desasignados (pérdidas) cuando el programa termina, de modo que no es necesario crear código para volcar objetos en ese punto.

El siguiente código prueba si existe pérdida de memoria comparando dos estados de la memoria y produce un volcado de memoria de todos los objetos si se detecta una pérdida.

```cpp
if( diffMemState.Difference( oldMemState, newMemState ) )
{
    TRACE( "Memory leaked!\n" );
    diffMemState.DumpAllObjectsSince();
}
```

El contenido del volcado de memoria presenta el siguiente aspecto:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

Los números entre llaves al principio de la mayoría de las líneas especifican el orden en que se asignaron los objetos. El objeto asignado más recientemente tiene el número más alto y aparece en la parte superior del volcado de memoria.

Para obtener la máxima información posible de un volcado de memoria de objetos, puede invalidar la función miembro `Dump` de cualquier objeto derivado de `CObject`para personalizar el volcado de memoria de objetos.

Puede establecer un punto de interrupción en una determinada asignación de memoria si asigna a la variable global `_afxBreakAlloc` el número mostrado entre llaves. Si vuelve a ejecutar el programa, el depurador interrumpirá la ejecución cuando se produzca la asignación. Entonces, puede examinar la pila de llamadas para ver cómo llegó el programa a ese punto.

La biblioteca en tiempo de ejecución de C dispone de una función similar, [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc), que se puede usar para las asignaciones en tiempo de ejecución de C.

[En este tema](#BKMK_In_this_topic)

#### <a name="BKMK_Interpreting_memory_dumps"></a> Interpretar volcados de memoria
Examine el siguiente volcado de memoria de objetos con mayor detalle:

```cmd
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215

{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long
```

El programa que generó este volcado de memoria sólo tenía dos asignaciones de memoria explícitas: una en la pila y otra en el montón:

```cpp
// Do your memory allocations and deallocations.
CString s("This is a frame variable");
// The next object is a heap object.
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
```

El constructor `CPerson` recibe tres argumentos que son punteros a `char`y que se utilizan para inicializar variables miembro de `CString` . En el volcado de memoria, se puede ver el objeto `CPerson` junto con tres bloques que no corresponden a objetos (3, 4 y 5). Éstos contienen los caracteres para las variables miembro de `CString` y no se eliminarán cuando se llame al destructor del objeto `CPerson` .

El bloque número 2 es el propio objeto `CPerson` . `$51A4` representa la dirección del bloque y va seguida por el contenido del objeto, volcado por `CPerson`::`Dump` al ser invocado por [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince).

El bloque número 1 se encuentra asociado con la variable `CString` del marco de trabajo, como se puede ver por su número de secuencia y tamaño, que coincide con el número de caracteres de la variable `CString` del marco. Las variables asignadas en el marco de trabajo se desasignan automáticamente cuando el marco se sale del ámbito.

**Variables de marco**

En general, no debería preocuparse de los objetos del montón asociados con variables de marco, ya que se desasignan automáticamente cuando las variables se salen de su ámbito. Para conseguir claridad y orden en los volcados de memoria, las llamadas a `Checkpoint` se deberían colocar de modo que se encuentren fuera del ámbito de las variables de marco. Por ejemplo, coloque el código de asignación anterior entre llaves de ámbito, como se muestra a continuación:

```cpp
oldMemState.Checkpoint();
{
    // Do your memory allocations and deallocations ...
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
}
newMemState.Checkpoint();
```

Con las llaves de ámbito, el volcado de memoria quedaría así:

```cmd
Dumping objects ->

{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long
{2} a CPerson at $51A4

Last Name: Smith
First Name: Alan
Phone #: 581-0215
```

**Asignaciones de elementos que no son objetos**

Observe que algunas asignaciones corresponden a objetos (como `CPerson`) y otras son asignaciones de elementos que no son objetos. "Asignaciones de elementos que no son objetos" son asignaciones de objetos que no derivan de `CObject` o asignaciones de tipos C primitivos como `char`, `int`o `long`. Si la clase derivada de <strong>CObject</strong>asigna espacio adicional, como para los búferes internos, esos objetos mostrarán asignaciones de objetos y de elementos que no son objetos.

**Evitar pérdidas de memoria**

Observe en el código anterior que el bloque de memoria asociado a la variable de marco `CString` se desasignó automáticamente y no aparece como pérdida de memoria. La desasignación automática asociada a las reglas de ámbito se ocupa de la mayoría de las pérdidas de memoria relacionadas con variables de marco.

Sin embargo, para objetos asignados en el montón, se debe eliminar explícitamente cada objeto para evitar una pérdida de memoria. Para evitar la última pérdida de memoria del ejemplo anterior, elimine el objeto `CPerson` asignado en el montón, como se indica a continuación:

```cpp
{
    // Do your memory allocations and deallocations.
    CString s("This is a frame variable");
    // The next object is a heap object.
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );
    delete p;
}
```

[En este tema](#BKMK_In_this_topic)

#### <a name="BKMK_Customizing_object_dumps"></a> Personalizar volcados de memoria de objetos
Si se deriva una clase de [CObject](/cpp/mfc/reference/cobject-class), puede reemplazarse la función miembro `Dump` para ofrecer información adicional cuando se utiliza [DumpAllObjectsSince](/cpp/mfc/reference/cmemorystate-structure#dumpallobjectssince) para realizar un volcado de memoria de objetos en la [Ventana de salida](../ide/reference/output-window.md).

La función `Dump` escribe una representación textual de las variables miembro del objeto en un contexto de volcado de memoria ([CDumpContext](/cpp/mfc/reference/cdumpcontext-class)). El contexto de volcado de memoria es similar a una secuencia de E/S. Se puede utilizar el operador de anexión ( **<<** para enviar datos a un `CDumpContext`.

Cuando se reemplaza la función `Dump` , primero se debería llamar a la versión de la clase base de `Dump` para realizar un volcado de memoria del contenido del objeto de la clase base. A continuación, se escribe una descripción textual y un valor descriptivo para cada variable miembro de la clase derivada.

La declaración de la función `Dump` presenta el siguiente aspecto:

```cpp
class CPerson : public CObject
{
public:
#ifdef _DEBUG
    virtual void Dump( CDumpContext& dc ) const;
#endif

    CString m_firstName;
    CString m_lastName;
    // And so on...
};
```

Como el volcado de objetos sólo tiene sentido en la depuración del programa, la declaración de la función `Dump` se encuentra encerrada en un bloque **#ifdef _DEBUG / #endif** .

En el siguiente ejemplo, la función `Dump` llama primero a la función `Dump` para su clase base. A continuación, escribe una breve descripción de cada variable miembro, junto con el valor del miembro, en la secuencia de diagnóstico.

```cpp
#ifdef _DEBUG
void CPerson::Dump( CDumpContext& dc ) const
{
    // Call the base class function first.
    CObject::Dump( dc );

    // Now do the stuff for our specific class.
    dc << "last name: " << m_lastName << "\n"
        << "first name: " << m_firstName << "\n";
}
#endif
```

Se debe suministrar un argumento `CDumpContext` que especifique dónde se escribirá el resultado del volcado de memoria. La versión de depuración de MFC suministra un objeto `CDumpContext` predefinido denominado `afxDump` que envía los resultados al depurador.

```cpp
CPerson* pMyPerson = new CPerson;
// Set some fields of the CPerson object.
//...
// Now dump the contents.
#ifdef _DEBUG
pMyPerson->Dump( afxDump );
#endif
```

[En este tema](#BKMK_In_this_topic)

## <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Reducir el tamaño de una configuración de compilación de MFC
La información de depuración para una aplicación MFC extensa puede ocupar un gran espacio en disco. Puede utilizar uno de estos procedimientos para reducir el tamaño:

1. Volver a generar las bibliotecas MFC usando la [/Z7, / Zi, /ZI (formato de la información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format) opción, en lugar de **/Z7**. Estas opciones compilan un único archivo de base de datos de programa (PDB) que contiene información de depuración para toda la biblioteca, lo que permite reducir información redundante y ahorrar espacio.

2. Recompile las bibliotecas MFC sin información de depuración (ninguna [/Z7, / Zi, /ZI (formato de la información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format) opción). En este caso, la falta de información de depuración impide utilizar la mayoría de los servicios del depurador dentro del código de la biblioteca MFC, pero, como estas bibliotecas ya están depuradas, eso no constituye ningún problema.

3. Compile su propia aplicación con información de depuración solo para los módulos seleccionados como se describe a continuación.

    [En este tema](#BKMK_In_this_topic)

### <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Compilar una aplicación MFC con la información de depuración para los módulos seleccionados
Compilar módulos seleccionados con las bibliotecas de depuración de MFC permite utilizar la ejecución paso a paso y otros servicios de depuración en esos módulos. Este procedimiento utiliza los modos de depuración y de lanzamiento del archivo MAKE de Visual C++, por lo que hace necesarios los cambios descritos en los pasos siguientes (y también "recompilar todo" cuando se requiere compilar una versión de lanzamiento completa).

1. En el Explorador de soluciones, seleccione el proyecto.

2. En el menú **Ver** , seleccione **Páginas de propiedades**.

3. Primero, se creará la configuración para un nuevo proyecto.

   1. En el cuadro de diálogo **\<Proyecto> Páginas de propiedades**, haga clic en el botón **Administrador de configuración**.

   2. En el [cuadro de diálogo Administrador de configuración](/previous-versions/visualstudio/visual-studio-2010/t1hy4dhz(v=vs.100)), localice el proyecto en la cuadrícula. En la columna **Configuración**, seleccione **\<Nueva...>** .

   3. En el [cuadro de diálogo Nueva configuración del proyecto](/previous-versions/visualstudio/visual-studio-2010/0eh8w4cf(v=vs.100)), escriba un nombre para la nueva configuración, como "Depuración parcial", en el cuadro **Nombre de configuración del proyecto** .

   4. En la lista **Copiar configuración de** , elija **Liberar**.

   5. Haga clic en **Aceptar** para cerrar el **nueva configuración del proyecto** cuadro de diálogo.

   6. Cierre el cuadro de diálogo **Administrador de configuración** .

4. A continuación, se establecerán opciones para todo el proyecto.

   1. En el cuadro de diálogo **Páginas de propiedades** , en la carpeta **Propiedades de configuración** , seleccione la categoría **General** .

   2. En la cuadrícula de configuración del proyecto, expanda **Valores predeterminados del proyecto** (si es necesario).

   3. En **Valores predeterminados del proyecto**, busque **Uso de MFC**. La configuración actual aparece en la columna derecha de la cuadrícula. Haga clic en la configuración actual y cámbiela a **Utilizar MFC en una biblioteca estática**.

   4. En el panel izquierdo del cuadro de diálogo **Páginas de propiedades** , abra la carpeta **C/C++** y seleccione **Preprocesador**. En la cuadrícula de propiedades, busque **Definiciones del preprocesador** y reemplace "NDEBUG" por "_DEBUG".

   5. En el panel izquierdo del cuadro de diálogo **Páginas de propiedades** , abra la carpeta **Vinculador** y seleccione la categoría **Entrada** . En la cuadrícula de propiedades, busque **Dependencias adicionales**. En el valor de configuración **Dependencias adicionales** , escriba "NAFXCWD.LIB" y "LIBCMT".

   6. Haga clic en **Aceptar** para guardar las nuevas opciones de compilación y cierre el cuadro de diálogo **Páginas de propiedades** .

5. En el menú **Compilar** , elija **Recompilar**. Este comando quita toda la información de depuración de los módulos, pero no afecta a la biblioteca MFC.

6. Ahora, se debe volver a agregar la información de depuración en los módulos seleccionados de la aplicación. Recuerde que sólo se pueden establecer puntos de interrupción y realizar otras funciones del depurador en módulos compilados con información de depuración. Para cada archivo de proyecto en el que desee incluir información de depuración, ejecute los siguientes pasos:

   1. En el Explorador de soluciones, abra la carpeta **Archivos de código fuente** situada bajo el proyecto.

   2. Seleccione el archivo en el que desea incluir información de depuración.

   3. En el menú **Ver** , seleccione **Páginas de propiedades**.

   4. En el cuadro de diálogo **Páginas de propiedades** , bajo la carpeta **Opciones de configuración** , abra la carpeta **C/C++** y seleccione la categoría **General** .

   5. En la cuadrícula de propiedades, busque **Formato de la información de depuración.**

   6. Haga clic en los valores de **Formato de la información de depuración** y seleccione la opción deseada (normalmente **/ZI**) para la información de depuración.

   7. Si está utilizando una aplicación generada con el Asistente para aplicaciones, o dispone de encabezados precompilados, deberá desactivar los encabezados precompilados o volver a compilarlos antes de compilar los otros módulos. Si no lo hace así, recibirá la advertencia C4650 y el mensaje de error C2855. Para desactivar los encabezados precompilados, cambie el valor de la opción **Crear o usar encabezados precompilados** en el cuadro de diálogo **\<Proyecto> Propiedades** (carpeta **Propiedades de configuración**, subcarpeta **C/C++** , categoría **Encabezados precompilados**).

7. En el menú **Compilar** , seleccione **Compilar** para recompilar los archivos del proyecto que no estén actualizados.

   Como alternativa a la técnica descrita en este tema, se puede utilizar un archivo MAKE externo para definir opciones individuales para cada archivo. En ese caso, para vincular con las bibliotecas de depuración de MFC, deberá definir el marcador [_DEBUG](/cpp/c-runtime-library/debug) para cada módulo. Si desea utilizar las bibliotecas de lanzamiento de MFC, debe definir NDEBUG. Para obtener más información sobre cómo escribir archivos MAKE externos, vea [Referencia de NMAKE](/cpp/build/running-nmake).

   [En este tema](#BKMK_In_this_topic)

## <a name="see-also"></a>Vea también
[Depurar en Visual C++](../debugger/debugging-native-code.md)
