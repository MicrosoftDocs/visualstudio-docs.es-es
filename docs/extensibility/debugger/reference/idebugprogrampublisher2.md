---
title: "IDebugProgramPublisher2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2"
helpviewer_keywords: 
  - "Interfaz IDebugProgramPublisher2"
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz permite un motor de depuración \(DE\) o proveedores de puerto personalizado de a los programas del registro para depurar.  
  
## Sintaxis  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## Notas para los implementadores  
 Visual Studio implementa esta interfaz para registrar los programas que se están depurando para crearlos visible para la depuración de varios procesos.  
  
## Notas para los llamadores  
 Función de `CoCreateInstance` de COM de llamada con `CLSID_ProgramPublisher` para obtener esta interfaz \(vea el ejemplo\).  Un OF o un proveedor de puerto utiliza esta interfaz para registrar los nodos del programa que representan los programas que se están depurando.  
  
## métodos en el orden de Vtable  
 Esta interfaz implementa los siguientes métodos:  
  
|Método|Descripción|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Coloca un nodo de programa a disposición del de y el administrador de depuración de la sesión \(SDM\).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Quita un nodo de programa para que ya no están disponibles.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Coloca un programa a disposición del de y el SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Quita un programa de modo que ya no está disponible.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Establece una marca que indica que un depurador está presente.|  
  
## Comentarios  
 Esta interfaz crea los programas y los nodos de programa disponibles \(es decir, “los publica”\) para uso de DES y administradores de depuración de la sesión \(SDM\).  Para tener acceso a los programas y nodos publicados del programa, utilice la interfaz de [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) .  Esta es la única forma Visual Studio puede reconocer que un programa está siendo depurado.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Ejemplo  
 Este ejemplo muestra cómo crear una instancia del editor del programa y registrar un nodo del programa.  Esto se toma del tutorial, [Publishing the Program Node](http://msdn.microsoft.com/es-es/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp#  
// This is how m_srpProgramPublisher is defined in the class definition:  
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.  
  
void CProgram::Start(IDebugEngine2 * pEngine)  
{  
    m_spEngine = pEngine;  
  
    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);  
        return;  
    }  
  
    // Register ourselves with the program publisher. Note that  
    // CProgram implements the IDebgProgramNode2 interface, hence  
    // the static cast on "this".  
    hr = m_srpProgramPublisher->PublishProgramNode(  
        static_cast<IDebugProgramNode2*>(this));  
    if ( FAILED(hr) )  
    {  
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);  
        m_srpProgramPublisher.Release();  
        return;  
    }  
  
    ATLTRACE("Added program node.\n");  
}  
```  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)