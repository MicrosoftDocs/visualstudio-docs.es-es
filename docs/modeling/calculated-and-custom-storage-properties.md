---
title: "Propiedades de almacenamiento personalizados y calculados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Lenguaje específico de dominio, propiedades de dominio de programación"
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
caps.handback.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propiedades de almacenamiento personalizados y calculados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Todas las propiedades de dominio en un lenguaje específico de dominio \(DSL\) se pueden mostrar al usuario en el diagrama y en el explorador del lenguaje y pueden obtener acceso al código de programa. Sin embargo, propiedades difieren en la forma en que se almacenan sus valores.  
  
## Tipos de propiedades del dominio  
 En la definición de DSL, puede establecer el **tipo** de una propiedad de dominio, como se muestra en la tabla siguiente:  
  
|Tipo de propiedad de dominio|Descripción|  
|----------------------------------|-----------------|  
|**Estándar** \(predeterminado\)|Una propiedad de dominio se guarda en el *almacenar* y serializado al archivo.|  
|**Calcula**|Una propiedad de dominio de sólo lectura que no se guarda en el almacén, pero se calcula a partir de otros valores.<br /><br /> Por ejemplo, `Person.Age` se ha podido calcular desde `Person.BirthDate`.<br /><br /> Se debe proporcionar el código que realiza el cálculo. Normalmente, se calcula el valor de otras propiedades de dominio. Sin embargo, también puede utilizar los recursos externos.|  
|**Almacenamiento personalizado**|Una propiedad de dominio que no se guarda directamente en el almacén, pero puede ser get y set.<br /><br /> Se debe proporcionar los métodos que obtienen y establecen el valor.<br /><br /> Por ejemplo, `Person.FullAddress` podría almacenarse en `Person.StreetAddress`, `Person.City`, y `Person.PostalCode`.<br /><br /> También puede tener acceso a recursos externos como, por ejemplo, para obtener y establecer valores de una base de datos.<br /><br /> El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Consulte [transacciones y establecedores personalizados](#setters).|  
  
## Proporciona el código para una propiedad calculada o personalizados de almacenamiento  
 Si establece el tipo de una propiedad de dominio calculado o almacenamiento personalizado, tiene que proporcionar métodos de acceso. Cuando se compila una solución, un informe de errores le indicará lo que se requiere.  
  
#### Para definir una calculado o propiedad de almacenamiento personalizado  
  
1.  En DslDefinition.dsl, seleccione la propiedad de dominio en el diagrama o en **DSL Explorer**.  
  
2.  En el **propiedades** ventana, establezca el **tipo** campo **calculado** o **almacenamiento personalizado**.  
  
     Asegúrese de que ha establecido su **tipo** que desee.  
  
3.  Haga clic en **Transformar todas las plantillas** en la barra de herramientas de **el Explorador de soluciones**.  
  
4.  En el menú **Compilar**, haga clic en **Compilar solución**.  
  
     Recibirá el siguiente mensaje de error: "*Suclase* no contiene una definición para Get*YourProperty*."  
  
5.  Haga doble clic en el mensaje de error.  
  
     Se abrirá DomainRelationships.cs o Dsl\\GeneratedCode\\DomainClasses.cs. Por encima de la llamada de método resaltada, un comentario le pide que proporcione una implementación para Get*YourProperty*\(\).  
  
    > [!NOTE]
    >  Este archivo se genera a partir de DslDefinition.dsl. Si edita este archivo, los cambios se perderán la próxima vez que se hace clic **Transformar todas las plantillas**. En su lugar, agregue el método requerido en un archivo independiente.  
  
6.  Cree o abra un archivo de clase en una carpeta independiente, por ejemplo CustomCode\\*YourDomainClass*. cs.  
  
     Asegúrese de que el espacio de nombres es el mismo que el código generado.  
  
7.  En el archivo de clase, escribir una implementación parcial de la clase de dominio. En la clase, escribir una definición de la falta `Get` método similar al ejemplo siguiente:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Si establece **tipo** a **almacenamiento personalizado**, también tendrá que proporcionar un `Set` \(método\). Por ejemplo:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     El código no debe establecer valores en el almacén cuando `Store.InUndoRedoOrRollback` es true. Consulte [transacciones y establecedores personalizados](#setters).  
  
9. Compile y ejecute la solución.  
  
10. Probar la propiedad. Asegúrese de que intente **Deshacer** y **Rehacer**.  
  
##  <a name="setters"></a> Las transacciones y establecedores personalizados  
 En el método Set de la propiedad de almacenamiento personalizado, no tendrá que abrir una transacción, ya que normalmente se llama al método dentro de una transacción activa.  
  
 Sin embargo, el método Set también podría llamarse si el usuario invoca deshacer o rehacer, o si se revierte una transacción. Cuando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> es true, el método Set debe comportarse como sigue:  
  
-   No debe realizar cambios en el almacén, como la asignación de valores a otras propiedades de dominio. El Administrador de deshacer establece sus valores.  
  
-   Sin embargo, deben actualizar los recursos externos, como los objetos fuera de la tienda o contenido del archivo o base de datos. Esto asegurará que se mantienen en synchronism con los valores en el almacén.  
  
 Por ejemplo:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Para obtener más información acerca de las transacciones, consulte [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Vea también  
 [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Propiedades de las propiedades de dominio](../modeling/properties-of-domain-properties.md)   
 [Cómo: Definir lenguajes específicos de dominio](../modeling/how-to-define-a-domain-specific-language.md)