---
title: "Compatibilidad con la barra de navegaci&#243;n en un servicio de lenguaje heredado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Barra de exploración, auxiliares en servicios de lenguaje [managed package framework]"
  - "barra de navegación, de servicios de lenguaje [managed package framework]"
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Compatibilidad con la barra de navegaci&#243;n en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La barra de navegación en la parte superior de la vista de editor muestra los tipos y miembros en el archivo.  Muestra los tipos en el desplegable izquierda, y muestra los miembros de la derecha desplegable.  Cuando el usuario selecciona un tipo, el símbolo de intercalación se coloca en la primera línea del tipo.  Cuando el usuario selecciona un miembro, el símbolo de intercalación se coloca en la definición de miembros.  Las listas desplegables se actualizan para reflejar la ubicación del símbolo de intercalación actual.  
  
## Mostrar y actualizar la barra de navegación  
 Para admitir la barra de navegación, debe derivar una clase de la clase de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> e implementar el método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .  Cuando el servicio de lenguaje tiene una ventana de código, la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> de base crea instancias <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, que contiene el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> que representa la ventana de código.  El objeto de <xref:Microsoft.VisualStudio.Package.CodeWindowManager> se asigna un nuevo objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  El método de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> obtiene un objeto de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> .  Si devuelve una instancia de la clase de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> , <xref:Microsoft.VisualStudio.Package.CodeWindowManager> llama al método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> para rellenar las listas internas y pasa el objeto de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> el administrador desplegable de la barra de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  El administrador desplegable de la barra, a su vez, llama al método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> en el objeto de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> para establecer el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>que contiene las dos barras desplegables.  
  
 Cuando el símbolo de intercalación se mueve, las llamadas al método de <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> el método de <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> .  Las llamadas al método bases de <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> el método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> en la clase de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> para actualizar el estado de la barra de navegación.  Se pasa un conjunto de objetos de <xref:Microsoft.VisualStudio.Package.DropDownMember> a este método.  Cada objeto representa una entrada en la lista desplegable.  
  
## El contenido de la barra de navegación  
 La barra de navegación normalmente contiene una lista de tipos y una lista de miembros.  La lista de tipos incluye todos los tipos disponibles en el archivo de código fuente actual.  Los nombres de tipos incluyen toda la información de espacio de nombres.  A continuación se muestra un ejemplo de código de C\# con dos tipos:  
  
```c#  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 La lista de tipos mostrará `TestLanguagePackage.TestLanguageService` y `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 La lista de miembros muestra los miembros disponibles del tipo que se seleccione en la lista de tipos.  En el ejemplo de código anterior, si `TestLanguagePackage.TestLanguageService` es el tipo que está seleccionado, la lista de miembros contendría los miembros privados `tokens` y `serviceName`.  La estructura interna `Token` no se muestra.  
  
 Puede implementar la lista de miembros para crear el nombre de un miembro negrita cuando el símbolo de intercalación se coloca dentro de.  Los miembros también pueden mostrados en atenuado out text, que indica que no están dentro del ámbito en el símbolo de intercalación se coloca actualmente.  
  
## Habilitar la compatibilidad con la barra de navegación  
 Para habilitar la compatibilidad con la barra de navegación, debe establecer el parámetro de `ShowDropdownBarOption` de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> a `true`.  Este parámetro establece la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>.  Para admitir la barra de navegación, debe implementar el objeto de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> en el método de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> .  
  
 En la implementación del método de <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> , si la propiedad de <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> se establece en `true`, puede devolver un objeto de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> .  Si no devuelve el objeto, la barra de navegación no se muestra.  
  
 La opción de mostrar la barra de navegación se puede establecer el usuario, lo que es posible que este control es restablecer mientras que la vista de editor abierta.  El usuario debe cerrar y volver a abrir la ventana del editor antes de que tenga lugar el cambio.  
  
## Implementar la compatibilidad para la barra de navegación  
 El método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> toma dos listas \(una para cada desplegable\) y dos valores que representan la selección actual en cada lista.  Las listas y los valores de selección pueden actualizarse, en cuyo caso el método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> debe devolver `true` para indicar que las listas han cambiado.  
  
 Como los cambios de selección en tipos desplegables, la lista de miembros debe actualizarse para reflejar el nuevo tipo.  Lo que se muestra en la lista de miembros puede ser:  
  
-   La lista de miembros para el tipo actual.  
  
-   Todos los miembros disponibles en el archivo de código fuente, pero con todos los miembros no en el tipo actual que se muestran en texto atenuado\-hacia fuera.  El usuario todavía puede seleccionar los miembros atenuados\-hacia fuera, por lo que pueden utilizarse para la navegación rápida, pero el color indica que no forman parte del tipo seleccionado.  
  
 Una implementación del método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> general realiza los pasos siguientes:  
  
1.  Obtener una lista de declaraciones actuales del archivo de código fuente.  
  
     hay varias maneras de rellenar las listas.  Un enfoque consiste en crear un método personalizado en la versión de la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> que llama al método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> con un motivo personalizada de análisis que devuelve una lista de todas las declaraciones.  Otro enfoque podría llamar al método de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> directamente del método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> con el motivo personalizada de análisis.  Un tercer enfoque podría ser almacenar en caché las declaraciones de la clase de <xref:Microsoft.VisualStudio.Package.AuthoringScope> devuelta por la operación completa del análisis en la clase de <xref:Microsoft.VisualStudio.Package.LanguageService> y recuperar que el método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .  
  
2.  rellene o actualice la lista de tipos.  
  
     El contenido de la lista de tipos pueden actualizarse cuando el origen ha cambiado o si decide cambiar el estilo del texto de los tipos basados en la posición del símbolo de intercalación actual.  Observe que esta posición se pasa al método de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .  
  
3.  Determine el tipo seleccionar en la lista de tipos basada en la posición del símbolo de intercalación actual.  
  
     Puede buscar las declaraciones que se recogieron en el paso 1 para encontrar el tipo que agrega la posición del símbolo de intercalación actual, y después buscan los tipos enumerados para que ese tipo determine su índice en la lista de tipos.  
  
4.  rellene o actualice la lista de miembros basados en el tipo seleccionado.  
  
     La lista de miembros refleja lo que se muestra actualmente en **miembros** desplegable.  El contenido de la lista de miembros necesiten actualizar si el origen ha cambiado o si se muestran sólo los miembros del tipo seleccionado y del tipo seleccionado ha cambiado.  Si decide mostrar todos los miembros en el archivo de código fuente, el estilo del texto de cada miembro en la lista es necesario actualizar si el tipo seleccionado ha cambiado.  
  
5.  Determine el miembro seleccionar en la lista de miembros basada en la posición del símbolo de intercalación actual.  
  
     Busque las declaraciones que se recogieron en el paso 1 para el miembro que contiene la posición actual del símbolo de intercalación, después busca la lista para que ese miembro determine su índice en la lista de miembros.  
  
6.  `true` return si se han realizado cambios en las listas o a las selecciones en cualquiera de las listas.