---
title: Ediciones no compatibles en Visual Basic, editar y continuar | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 94a151a7adab5c8246cec38c2e62d76788beb6e7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155432"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Ediciones no compatibles en Editar y continuar de Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La característica Editar y continuar permite detener la ejecución del programa en modo de interrupción, realizar cambios en el código en ejecución y retomar la ejecución del programa con estos nuevos cambios incorporados. Las modificaciones del código declarativo que afectan a la estructura pública de una clase suelen estar prohibidas, pero se permiten muchas modificaciones que se podrían hacer en un método, cuerpo de propiedad o declaraciones privadas en una clase.  
  
 Si necesita realizar un cambio no compatible, debe detener la depuración, hacer el cambio e iniciar una nueva sesión de depuración.  
  
### <a name="BKMK_MethodandPropertyBodyEdits"></a> Ediciones de cuerpo de la propiedad y método  
 **Cambios no admitidos en Variables locales estáticas**: Agregar o actualizar una variable local o quitar una variable local estática si eso provocara un error de compilación.  
  
 **Cambios no admitidos en los genéricos**: No se admiten cambios en el propio método genérico o en el cuerpo del método genérico. Se puede agregar, eliminar o cambiar la creación de instancias de un tipo genérico o de llamadas a los métodos genéricos existentes.  
  
 **Otros cambios no admitidos**  
  
- Cambiar la instrucción de invocación de un método que está en la pila de llamadas.  
  
- Agregar un bloque `Try...Catch` cuando el puntero de instrucción termina en el bloque `Catch` o en el bloque `Finally`.  
  
- Quitar un `Try...Catch` bloque, cuando el puntero de instrucción está en un `Catch`bloque o `Finally` bloque.  
  
- Agregar un bloque `Using` alrededor del puntero de instrucción actual.  
  
- Agregar un bloque `SynchLock` alrededor del puntero de instrucción actual.  
  
### <a name="BKMK_AttributeEdits"></a> Ediciones de atributos  
 Editar y continuar no admite la modificación de atributos. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Definir, editar o eliminar una clase de atributos.  
  
- Agregar un atributo.  
  
- Editar o quitar un atributo existente.  
  
### <a name="BKMK_ClassDeclarationEdits"></a> Ediciones de declaraciones de clase  
 Editar y continuar no permite la mayoría de los cambios en las declaraciones de clase en modo de interrupción. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Cambiar el nombre, eliminar o cambiar la herencia de una clase existente.  
  
- Implementar una nueva interfaz o quitar la implementación de una interfaz.  
  
- Cambiar los modificadores de una clase.  
  
- Agregar, cambiar o quitar el estado `ComClass`.  
  
- Editar cualquier declaración de clase genérica.  
  
### <a name="BKMK_ClassMemberDeclarationEdits"></a> Ediciones de declaraciones de miembro de clase  
 En la mayoría de los casos, las declaraciones de miembros están prohibidas en Editar y continuar. Por ejemplo, no puede cambiar la firma o el nivel de acceso de un miembro ni puede quitar completamente los miembros si eso provocara un error de compilación. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Sombrear una variable miembro existente mediante la declaración de una variable miembro o variable global con el mismo nombre en el bloque contenedor.  
  
- Ocultar una variable local estática mediante la declaración de una nueva instancia dentro de un bloque.  
  
- Quitar los controladores de un evento. Se permite agregar un controlador de eventos.  
  
- Agregar una nueva propiedad o método de sobrecarga, a menos que la propiedad o método sea `Private` y no aparezca su nombre en una instrucción activa.  
  
- Agregar o quitar la cláusula `WithEvents` en una variable miembro.  
  
- Eliminar un miembro.  
  
- Cambiar una declaración de método o propiedad para detener la implementación de una interfaz.  
  
- Modificar cualquier método que utilice tipos genéricos.  
  
- Cambiar la firma o tipo de valor devuelto de un método o propiedad no privados.  
  
- Reemplazar o sombrear un miembro de una clase base.  
  
- Agregar un campo nuevo en cualquier clase marcada con `SequentialLayout` o `ExplicitLayout`.  
  
- Cambiar el estado `MustInherit` o `NotOverridable` de un método.  
  
- Cambiar los modificadores de acceso de una propiedad o método.  
  
- Cambiar el tipo o el estado de solo lectura de un campo.  
  
- Cambiar un campo público.  
  
### <a name="BKMK_CompilerOptionEdits"></a> Ediciones de opciones del compilador  
 Mientras utilice Editar y continuar en modo de interrupción, no podrá cambiar, agregar o quitar las siguientes opciones del compilador:  
  
- **Option Strict**  
  
- **Option Explicit**  
  
- **Option Compare**  
  
### <a name="BKMK_ConstantsEdits"></a> Ediciones de constantes  
 Los cambios de las constantes en el modo Editar y continuar están muy limitados. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Agregar o actualizar una variable constante.  
  
- Cambiar el tipo o valor de una constante.  
  
- Quitar una constante.  
  
### <a name="BKMK_DelegateandEventDeclarationEdits"></a> Ediciones de declaraciones de evento y delegado  
 Editar y continuar no permite algunos de los cambios en los delegados y los eventos en el modo de interrupción. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Cambiar o eliminar una definición de delegado.  
  
- Eliminar un evento.  
  
### <a name="BKMK_EnumerationEdits"></a> Ediciones de enumeraciones  
 Editar y continuar no permite cambios en enumeraciones (`Enums`) en el modo de interrupción. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Modificar el tipo subyacente de un valor `Enum`.  
  
- Agregar, cambiar o quitar un miembro de `Enum`.  
  
- Cambiar el modificador de acceso de un valor `Enum`.  
  
### <a name="BKMK_ExternalDeclarationsEdits"></a> Ediciones de declaraciones externas  
 En general, no puede cambiar las declaraciones de métodos externos mientras se encuentra en modo Editar y continuar. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Agregar o quitar una declaración externa.  
  
- Cambiar la firma o serializar los atributos de una declaración externa.  
  
### <a name="BKMK_ImportsEdits"></a> Ediciones de importaciones  
 Editar y continuar no permite agregar, cambiar o quitar instrucciones `Imports` mientras se encuentra en el modo de interrupción.  
  
### <a name="BKMK_InterfaceDefinitionEdits"></a> Ediciones de definiciones de interfaz  
 Aunque generalmente se pueden realizar cambios en miembros que implementan interfaces; Editar y continuar no suele permitir cambios en definiciones de interfaz reales. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Agregar, cambiar o quitar miembros de interfaz.  
  
- Eliminar una interfaz existente.  
  
- Cambiar el modificador de acceso de una interfaz.  
  
- Cambiar la jerarquía de herencia de las interfaces.  
  
### <a name="BKMK_ModuleDeclarationEdits"></a> Ediciones de declaraciones de módulo  
 Editar y continuar no permite la mayoría de los cambios en las declaraciones de módulo mientras se encuentra en el modo de interrupción. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Crear un nuevo módulo.  
  
- Cambiar el nombre o eliminar un módulo existente.  
  
- Cambiar el modificador de acceso de un módulo.  
  
### <a name="BKMK_ModuleMemberDeclarationEdits"></a> Ediciones de declaraciones de miembros de módulo  
 Con Editar y continuar, puede realizar una serie de cambios en los miembros de módulo, como propiedades, métodos y campos, mientras se encuentra en el modo de interrupción. Sin embargo, no se admiten algunos cambios. En concreto, Editar y continuar no admite la adición, eliminación o cambio del tipo o firma de ningún miembro.  
  
 En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Agregar un nuevo miembro, a menos que no aparezca su nombre en ninguna instrucción activa.  
  
- Quitar una propiedad o método.  
  
- Cambiar la firma de una propiedad o método.  
  
- Agregar, cambiar el nombre, mover o eliminar un campo.  
  
- Modificar cualquier método que utilice tipos genéricos.  
  
- Cambiar los modificadores de acceso de una propiedad o método, por ejemplo, cambiar `Public` a `Private`.  
  
- Eliminar o cambiar el tipo de un campo existente.  
  
### <a name="BKMK_NestedTypeDeclarationEdits"></a> Ediciones de declaraciones de tipo anidado  
 Editar y continuar no admite mover un tipo anidado a otro espacio de nombres o tipo.  
  
### <a name="BKMK_StructureDeclarationEdits"></a> Ediciones de declaraciones de estructura  
 La mayoría de los cambios en las declaraciones de estructura no se permiten editar y continuar mientras en **interrumpir** modo. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Cambiar el nombre o eliminar una estructura existente.  
  
- Implementar una nueva interfaz o quitar la implementación de una interfaz.  
  
- Cambiar el modificador de acceso de una estructura.  
  
### <a name="BKMK_StructureMemberDeclarationEdits"></a> Ediciones de declaraciones de miembros de estructura  
 Con Editar y continuar, es posible realizar una serie de cambios en miembros de estructura (propiedades, métodos y campos) mientras se está en el modo de interrupción. Sin embargo, no se admiten algunos los cambios, en concreto los que afectan a la declaración de miembros de estructura. En concreto, Editar y continuar no admite los siguientes cambios:  
  
- Quitar una propiedad o método.  
  
- Agregar o quitar un campo.  
  
- Cambiar la firma de una propiedad o método.  
  
- Modificar cualquier método que utilice tipos genéricos.  
  
- Cambiar si una declaración de método o propiedad implementa una interfaz.  
  
- Cambiar los modificadores de acceso de un método o propiedad (por ejemplo, cambiar `Public` a **privada**).  
  
- Quitar un campo.  
  
- Cambiar el tipo de un campo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Aplicar tareas de edición en modo de interrupción con Editar y continuar](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Editar y continuar (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
