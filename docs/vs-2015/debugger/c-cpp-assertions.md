---
title: Las aserciones de C/C ++ | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3dc4c2a6c4f5b9d4a0e4e1cf0fd0a4a6c9928de6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51799761"
---
# <a name="cc-assertions"></a>Aserciones de C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una instrucción de aserción especifica una condición que se espera que sea cierta (valor true) en un punto del programa. Si esa condición no es true, la aserción produce un error, se interrumpe la ejecución del programa y el [cuadro de diálogo de error de aserción](../debugger/assertion-failed-dialog-box.md) aparece.  

 Visual C++ admite instrucciones de aserción que se basan en los constructores siguientes:  

- Aserciones de MFC para programas.  

- [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) para programas que utilizan ATL.  

- Aserciones de CRT para programas que utilizan la biblioteca en tiempo de ejecución de C.  

- El ANSI [función assert](http://msdn.microsoft.com/library/a9ca031a-648b-47a6-bdf1-65fc7399dd40) para otros programas de C o C++.  

  Se pueden utilizar aserciones para detectar errores lógicos, comprobar resultados de una operación y probar condiciones de error que deben haberse controlado.  

##  <a name="BKMK_In_this_topic"></a> En este tema  
 [Cómo funcionan las aserciones](#BKMK_How_assertions_work)  

 [Aserciones en compilaciones de depuración y lanzamiento](#BKMK_Assertions_in_Debug_and_Release_builds)  

 [Efectos del uso de aserciones](#BKMK_Side_effects_of_using_assertions)  

 [Aserciones de CRT](#BKMK_CRT_assertions)  

 [Aserciones de MFC](#BKMK_MFC_assertions)  

- [MFC ASSERT_VALID y CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)  

- [Limitaciones de AssertValid](#BKMK_Limitations_of_AssertValid)  

  [Usar aserciones](#BKMK_Using_assertions)  

- [Capturar errores lógicos](#BKMK_Catching_logic_errors)  

- [Comprobar resultados](#BKMK_Checking_results_)  

- [Buscar errores no controlados](#BKMK_Testing_error_conditions_)  

##  <a name="BKMK_How_assertions_work"></a> Cómo funcionan las aserciones  
 Cuando el depurador se detiene debido a una aserción de MFC o de la biblioteca en tiempo de ejecución de C, si el código fuente está disponible, navega hasta el punto del archivo de código fuente donde ocurrió la aserción. El mensaje de aserción aparece tanto en el [ventana de salida](../ide/reference/output-window.md) y **error de aserción** cuadro de diálogo. Puede copiar el mensaje de aserción de la **salida** ventana a una ventana de texto si desea guardarla para futuras referencias. El **salida** ventana puede contener también otros mensajes de error. Examine estos mensajes con cuidado, ya que pueden proporcionar pistas para encontrar la causa del error de aserción.  

 Use aserciones para detectar errores durante el desarrollo. En general, utilice una aserción para cada suposición. Por ejemplo, si supone que un argumento no es NULL, utilice una aserción para comprobar esa suposición.  

 [En este tema](#BKMK_In_this_topic)  

##  <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Aserciones en compilaciones de depuración y lanzamiento  
 Las instrucciones de aserción solo se compilan si se define `_DEBUG`. De lo contrario, el compilador trata las aserciones como instrucciones NULL. Por tanto, las instrucciones de aserción no imponen ninguna sobrecarga ni costo de rendimiento sobre la versión final del programa y permiten evitar utilizar el uso de directivas de `#ifdef`.  

##  <a name="BKMK_Side_effects_of_using_assertions"></a> Efectos del uso de aserciones  
 Cuando agregue aserciones al código, asegúrese de que no producen efectos secundarios. Por ejemplo, considere la siguiente aserción que modifica el valor `nM`:  

```  
ASSERT(nM++ > 0); // Don't do this!  

```  

 Como la expresión `ASSERT` no se evalúa en la versión de lanzamiento del programa, `nM` tendrá valores diferentes en las versiones de depuración (Debug) y de versión (Release). Para evitar este problema en MFC, puede usar el [compruebe](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) macro en lugar de `ASSERT`.  `VERIFY` evalúa la expresión en todas las versiones pero no comprueba el resultado en la versión de lanzamiento.  

 Tenga especial cuidado al utilizar llamadas a funciones en las instrucciones de aserción, ya que la evaluación de una función puede producir efectos laterales inesperados.  

```  
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects  
VERIFY ( myFnctn(0)==1 ) // safe  
```  

 `VERIFY` llama a `myFnctn` en ambas versiones, de depuración y lanzamiento, por lo que su uso es aceptable. No obstante, el uso de `VERIFY` impone la sobrecarga de una llamada de función innecesaria en la versión de lanzamiento.  

 [En este tema](#BKMK_In_this_topic)  

##  <a name="BKMK_CRT_assertions"></a> Aserciones de CRT  
 El CRTDBG. H define la [macros _ASSERT y _ASSERTE](http://msdn.microsoft.com/library/e98fd2a6-7f5e-4aa8-8fe8-e93490deba36) para comprobar aserciones.  


|   Macro    |                                             Resultado                                              |
|------------|-------------------------------------------------------------------------------------------------|
| `_ASSERT`  | Si la expresión especificada se evalúa como FALSE, el resultado es el nombre de archivo y el número de línea de la expresión sometida a `_ASSERT`. |
| `_ASSERTE` |      Igual que `_ASSERT`, más una representación de cadena de la expresión sometida a aserción.       |

 `_ASSERTE` es más eficaz, ya que informa de la expresión sometida a aserción que resultó ser falsa (valor FALSE). Esto puede ser suficiente para identificar el problema sin consultar el código fuente. No obstante, la versión de depuración de la aplicación contiene una constante de tipo cadena para cada expresión sometida a aserción mediante `_ASSERTE`. Si se utilizan muchas macros `_ASSERTE`, estas expresiones de cadena ocupan una cantidad de memoria significativa. Si eso constituye un problema, utilice `_ASSERT` para ahorrar memoria.  

 Cuando se define `_DEBUG`, la macro `_ASSERTE` se define del siguiente modo:  

```  
#define _ASSERTE(expr) \  
   do { \  
      if (!(expr) && (1 == _CrtDbgReport( \  
         _CRT_ASSERT, __FILE__, __LINE__, #expr))) \  
         _CrtDbgBreak(); \  
   } while (0)  
```  

 Si la expresión sometida a aserción se evalúa como FALSE, [_CrtDbgReport](http://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) se llama para notificar el error de aserción (mediante un cuadro de diálogo de mensaje de forma predeterminada). Si elige **vuelva a intentar** en el cuadro de diálogo de mensaje, `_CrtDbgReport` devuelve 1 y `_CrtDbgBreak` llama al depurador mediante `DebugBreak`.  

### <a name="checking-for-heap-corruption"></a>Comprobar si el montón está dañado  
 En el ejemplo siguiente se usa [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765) para comprobar si los daños del montón:  

```  
_ASSERTE(_CrtCheckMemory());  
```  

### <a name="checking-pointer-validity"></a>Comprobar la validez de los punteros  
 En el ejemplo siguiente se usa [_CrtIsValidPointer](http://msdn.microsoft.com/library/91c35590-ea5e-450f-a15d-ad8d62ade1fa) para comprobar que un determinado intervalo de memoria es válido para lectura o escritura.  

```  
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );  
```  

 En el ejemplo siguiente se usa [_CrtIsValidHeapPointer](http://msdn.microsoft.com/library/caf597ce-1b05-4764-9f37-0197a982bec5) para comprobar un puntero apunta a la memoria en el montón local (el montón creado y administrado por esta instancia de la biblioteca de tiempo de ejecución de C, un archivo DLL puede tener su propia instancia de la biblioteca, y por lo tanto, su propio montón, independiente del montón de la aplicación). Esta aserción captura no solo direcciones null o fuera de límites, sino también punteros a variables estáticas, variables de pila y cualquier otra memoria no local.  

```  
_ASSERTE(_CrtIsValidPointer( myData );  
```  

### <a name="checking-a-memory-block"></a>Comprobar un bloque de memoria  
 En el ejemplo siguiente se usa [_CrtIsMemoryBlock](http://msdn.microsoft.com/library/f7cbbc60-3690-4da0-a07b-68fd7f250273) para comprobar que un bloque de memoria se encuentra en el montón local y tiene un tipo de bloque válido.  

```  
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));  
```  

 [En este tema](#BKMK_In_this_topic)  

##  <a name="BKMK_MFC_assertions"></a> Aserciones de MFC  
 MFC define la [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) macro para comprobar aserciones. También define los métodos `MFC ASSERT_VALID` y `CObject::AssertValid` para comprobar el estado interno de un objeto derivado de `CObject`.  

 Si el argumento de la macro `ASSERT` de MFC se evalúa como cero o false, la macro detiene la ejecución del programa y alerta al usuario; de lo contrario, la ejecución continúa.  

 Cuando se produce un error de aserción, un cuadro de mensaje muestra el nombre del archivo de código fuente y el número de línea de la aserción. Si se elige Reintentar en el cuadro de diálogo cuadro, una llamada a [AfxDebugBreak](http://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) hace que la ejecución se interrumpa al depurador. En ese punto, se puede examinar la pila de llamadas y utilizar otros servicios del depurador para determinar la causa de la aserción. Si ha habilitado [Just-in-time depuración](../debugger/just-in-time-debugging-in-visual-studio.md)y ya no se estaba ejecutando el depurador, el cuadro de diálogo puede iniciar el depurador.  

 En el ejemplo siguiente se muestra cómo utilizar `ASSERT` para comprobar el valor devuelto de una función:  

```  
int x = SomeFunc(y);  
ASSERT(x >= 0);   //  Assertion fails if x is negative  
```  

 Puede utilizar ASSERT con la [IsKindOf](http://msdn.microsoft.com/library/7c87c748-b7e0-4c6d-9694-6035e62fdfd6) función para proporcionar comprobación de tipos de argumentos de función:  

```  
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );  
```  

 La macro `ASSERT` no produce código en la versión de lanzamiento. Si necesita evaluar la expresión en la versión de lanzamiento, utilice la [compruebe](http://msdn.microsoft.com/library/3e1ab4ee-cbc7-4290-a777-c92f42ce7b96) macro en lugar de ASSERT.  

###  <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID y CObject:: AssertValid  
 El [CObject:: AssertValid](http://msdn.microsoft.com/library/534a0744-4ab6-423d-b492-b4058b3d5157) método proporciona comprobaciones en tiempo de ejecución del estado interno de un objeto. Aunque no es obligatorio reemplazar `AssertValid` al derivar la clase de `CObject`, puede conseguir una clase más confiable si lo hace. `AssertValid` debe realizar aserciones en todas variables miembro del objeto para comprobar que contienen valores válidos. Por ejemplo, debería comprobar que las variables miembro no sean NULL.  

 En el ejemplo siguiente, se muestra cómo declarar una función `AssertValid`:  

```  
class CPerson : public CObject  
{  
protected:  
    CString m_strName;  
    float   m_salary;  
public:  
#ifdef _DEBUG  
    // Override  
    virtual void AssertValid() const;  
#endif  
    // ...  
};  

```  

 Cuando invalide `AssertValid`, llame a la versión de la clase base de `AssertValid` antes de ejecutar sus propias comprobaciones. Después, use la macro ASSERT para comprobar los miembros únicos de la clase derivada, como se muestra a continuación:  

```  
#ifdef _DEBUG  
void CPerson::AssertValid() const  
{  
    // Call inherited AssertValid first.  
    CObject::AssertValid();  

    // Check CPerson members...  
    // Must have a name.  
    ASSERT( !m_strName.IsEmpty());  
    // Must have an income.  
    ASSERT( m_salary > 0 );  
}  
#endif  

```  

 Si cualquiera de las variables miembro almacenan objetos, se puede utilizar la macro `ASSERT_VALID` para probar su validez interna (si sus clases reemplazan la función `AssertValid`).  

 Por ejemplo, considere la posibilidad de una clase `CMyData`, que almacena un [CObList](http://msdn.microsoft.com/library/80699c93-33d8-4f8b-b8cf-7b58aeab64ca) en uno de sus variables miembro. La variable `CObList`, `m_DataList`, almacena una colección de objetos `CPerson`. Una declaración abreviada de `CMyData` tiene el siguiente aspecto:  

```  
class CMyData : public CObject  
{  
    // Constructor and other members ...  
    protected:  
        CObList* m_pDataList;  
    // Other declarations ...  
    public:  
#ifdef _DEBUG  
        // Override:  
        virtual void AssertValid( ) const;  
#endif  
    // And so on ...  
};  

```  

 El sustituto de `AssertValid` en `CMyData` es:  

```  
#ifdef _DEBUG  
void CMyData::AssertValid( ) const  
{  
    // Call inherited AssertValid.  
    CObject::AssertValid( );  
    // Check validity of CMyData members.  
    ASSERT_VALID( m_pDataList );  
    // ...  
}  
#endif  

```  

 `CMyData` utiliza el mecanismo `AssertValid` para probar la validez de los objetos almacenados en su miembro de datos. El sustituto `AssertValid` de `CMyData` invoca la macro `ASSERT_VALID` para su propia variable miembro m_pDataList.  

 Las pruebas de validez no se detienen en este nivel, ya que la clase `CObList` también reemplaza la función `AssertValid`. Esta sustitución ejecuta pruebas de validez adicionales sobre el estado interno de la lista. Así, una prueba de validez sobre un objeto `CMyData` conduce a pruebas de validez adicionales sobre los estados internos del objeto de lista `CObList` almacenado.  

 Con algo más de trabajo, se podrían también agregar pruebas de validez para los objetos `CPerson` almacenados en la lista. Se podría derivar una clase `CPersonList` de `CObList` y reemplazar `AssertValid`. En el método reemplazado, se llamaría a `CObject::AssertValid` y, a continuación, la lista se recorrería en iteración, llamando a `AssertValid` para cada objeto `CPerson` almacenado en la lista. La clase `CPerson` mostrada al principio de este tema ya reemplaza la función `AssertValid`.  

 Se trata de un mecanismo muy eficaz de las versiones de depuración. Cuando, posteriormente, se compilan versiones de lanzamiento, el mecanismo se desactiva automáticamente.  

###  <a name="BKMK_Limitations_of_AssertValid"></a> Limitaciones de AssertValid  
 Si se desencadena una aserción, el objeto es definitivamente defectuoso y la ejecución se detendrá. Sin embargo, una falta de aserción solo indica que no se encontró ningún problema, pero no garantiza que el objeto sea correcto.  

 [En este tema](#BKMK_In_this_topic)  

##  <a name="BKMK_Using_assertions"></a> Usar aserciones  

###  <a name="BKMK_Catching_logic_errors"></a> Capturar errores lógicos  
 Se puede definir una aserción sobre una condición que debe ser cierta según la lógica del programa. La aserción no tiene ningún efecto a menos que se produzca un error de lógica.  

 Por ejemplo, suponga que está simulando moléculas de gas en un contenedor y que la variable `numMols` representa el número total de moléculas. Este número no puede ser menor que cero, por tanto, se podría incluir una instrucción de aserción de MFC como esta:  

```  
ASSERT(numMols >= 0);  

```  

 O bien, podría incluir una aserción de CRT como esta:  

```  
_ASSERT(numMols >= 0);  
```  

 Estas instrucciones no hacen nada si el programa funciona correctamente. Si un error lógico hace `numMols` sea menor que cero, sin embargo, la aserción detiene la ejecución del programa y muestra el [cuadro de diálogo de error de aserción](../debugger/assertion-failed-dialog-box.md).  

 [En este tema](#BKMK_In_this_topic)  

###  <a name="BKMK_Checking_results_"></a> Comprobar resultados  
 Las aserciones son valiosas para probar operaciones cuyos resultados no son obvios con una simple inspección visual.  

 Por ejemplo, considere el siguiente código, que actualiza la variable `iMols` según el contenido de la lista vinculada a la que apunta `mols`:  

```  
/* This code assumes that type has overloaded the != operator  
 with const char *   
It also assumes that H2O is somewhere in that linked list.   
Otherwise we'll get an access violation... */  
while (mols->type != "H2O")  
{  
 iMols += mols->num;  
 mols = mols->next;  
}  
ASSERT(iMols<=numMols); // MFC version  
_ASSERT(iMols<=numMols); // CRT version  
```  

 El número de moléculas contadas por `iMols` debe ser siempre menor o igual que el número total de moléculas, `numMols`. La inspección visual del bucle no muestra que este sea necesariamente el caso, por lo que se utiliza una instrucción de aserción después del bucle para probar esa condición.  

 [En este tema](#BKMK_In_this_topic)  

###  <a name="BKMK_Testing_error_conditions_"></a> Buscar errores no controlados  
 Se pueden utilizar aserciones para probar condiciones de error en un punto del código en el que cualquier error se debería haber controlado. En el siguiente ejemplo, una rutina gráfica devuelve cero si no hay error, o un código de error, en caso contrario.  

```  
myErr = myGraphRoutine(a, b);  

/* Code to handle errors and  
   reset myErr if successful */  

ASSERT(!myErr); -- MFC version  
_ASSERT(!myErr); -- CRT version  
```  

 Si el código de tratamiento del error funciona correctamente, el error debería recibir el tratamiento adecuado y `myErr` se debería restablecer a cero antes de alcanzar la aserción. Si `myErr` tiene otro valor, la aserción, produce un error, el programa se detiene y la [cuadro de diálogo de error de aserción](../debugger/assertion-failed-dialog-box.md) aparece.  

 No obstante, las instrucciones de aserción no son un sustituto del código de control de errores. El siguiente ejemplo muestra una instrucción de aserción que puede causar problemas en el código final de la versión de lanzamiento:  

```  
myErr = myGraphRoutine(a, b);  

/* No Code to handle errors */  

ASSERT(!myErr); // Don't do this!  
_ASSERT(!myErr); // Don't do this, either!  
```  

 Este código se basa en la instrucción de aserción para controlar la condición de error. Como resultado, ningún código de error devuelto por `myGraphRoutine` dispondrá de tratamiento en el código de la versión de lanzamiento.  

 [En este tema](#BKMK_In_this_topic)  

## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Aserciones en el código administrado](../debugger/assertions-in-managed-code.md)



