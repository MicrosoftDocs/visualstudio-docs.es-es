---
title: Compatibilidad con la barra de navegación en un servicio de lenguaje heredado
description: Obtenga información sobre cómo admitir la barra de navegación en un servicio de lenguaje heredado. En la barra de navegación de la vista del editor se muestran los tipos y miembros del archivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e75103d008e65c6d2060d598e442499f38a0e322
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080663"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Compatibilidad con la barra de navegación en un servicio de lenguaje heredado
La barra de navegación de la parte superior de la vista del editor muestra los tipos y miembros del archivo. Los tipos se muestran en la lista desplegable izquierda y los miembros se muestran en la lista desplegable derecha. Cuando el usuario selecciona un tipo, el símbolo de intercalación se coloca en la primera línea del tipo. Cuando el usuario selecciona un miembro, el símbolo de intercalación se coloca en la definición del miembro. Los cuadros desplegables se actualizan para reflejar la ubicación actual del símbolo de intercalación.

## <a name="displaying-and-updating-the-navigation-bar"></a>Mostrar y actualizar la barra de navegación
 Para admitir la barra de navegación, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase e implementar el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método. Cuando el servicio de lenguaje recibe una ventana de código, la <xref:Microsoft.VisualStudio.Package.LanguageService> clase base crea una instancia de <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , que contiene el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> objeto que representa la ventana de código. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>A continuación, el objeto recibe un nuevo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> objeto. El <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método obtiene un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto. Si devuelve una instancia de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase, llama al <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método para rellenar las listas internas y pasa el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto al administrador de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra desplegable. A su vez, el administrador de la barra desplegable llama al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> método en el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto para establecer el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> objeto que contiene las dos barras desplegables.

 Cuando se mueve el símbolo de intercalación, el <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> método llama al <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> método. El <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> método base llama al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método de la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> clase para actualizar el estado de la barra de navegación. Se pasa un conjunto de <xref:Microsoft.VisualStudio.Package.DropDownMember> objetos a este método. Cada objeto representa una entrada en la lista desplegable.

## <a name="the-contents-of-the-navigation-bar"></a>Contenido de la barra de navegación
 Normalmente, la barra de navegación contiene una lista de tipos y una lista de miembros. La lista de tipos incluye todos los tipos disponibles en el archivo de código fuente actual. Los nombres de tipo incluyen la información de espacio de nombres completa. A continuación se proporciona un ejemplo de código de C# con dos tipos:

```csharp
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

 La lista tipo mostrará `TestLanguagePackage.TestLanguageService` y `TestLanguagePackage.TestLanguageService.Tokens` .

 La lista miembros muestra los miembros disponibles del tipo que está seleccionado en la lista tipos. Con el ejemplo de código anterior, si `TestLanguagePackage.TestLanguageService` es el tipo que está seleccionado, la lista de miembros contendría los miembros privados `tokens` y `serviceName` . `Token`No se muestra la estructura interna.

 Puede implementar la lista de miembros para poner en negrita el nombre de un miembro cuando el símbolo de intercalación se coloca dentro de él. Los miembros también se pueden mostrar en texto atenuado, lo que indica que no están dentro del ámbito en el que está situado actualmente el símbolo de intercalación.

## <a name="enabling-support-for-the-navigation-bar"></a>Habilitar la compatibilidad con la barra de navegación
 Para habilitar la compatibilidad con la barra de navegación, debe establecer el `ShowDropdownBarOption` parámetro del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo en `true` . Este parámetro establece la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Para admitir la barra de navegación, debe implementar el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto en el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase.

 En la implementación del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método, si la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> propiedad está establecida en `true` , se puede devolver un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> objeto. Si no devuelve el objeto, no se muestra la barra de navegación.

 El usuario puede establecer la opción para mostrar la barra de navegación, por lo que es posible restablecer este control mientras la vista del editor está abierta. El usuario debe cerrar y volver a abrir la ventana del editor antes de que tenga lugar el cambio.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementar la compatibilidad con la barra de navegación
 El <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método toma dos listas (una para cada lista desplegable) y dos valores que representan la selección actual en cada lista. Las listas y los valores de selección se pueden actualizar, en cuyo caso el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método debe devolver `true` para indicar que las listas han cambiado.

 A medida que cambia la selección en el menú desplegable tipos, la lista de miembros debe actualizarse para reflejar el nuevo tipo. Lo que se muestra en la lista de miembros puede ser:

- Lista de miembros para el tipo actual.

- Todos los miembros disponibles en el archivo de código fuente, pero con todos los miembros que no están en el tipo actual mostrados en texto atenuado. El usuario todavía puede seleccionar los miembros atenuados, por lo que se pueden usar para una navegación rápida, pero el color indica que no forman parte del tipo seleccionado actualmente.

  Una implementación del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método normalmente realiza los siguientes pasos:

1. Obtiene una lista de las declaraciones actuales del archivo de código fuente.

     Hay varias maneras de rellenar las listas. Un enfoque consiste en crear un método personalizado en la versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase que llama al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método con un motivo de análisis personalizado que devuelve una lista de todas las declaraciones. Otro enfoque podría ser llamar al <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> método directamente desde el <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método con el motivo del análisis personalizado. Un tercer enfoque podría ser almacenar en caché las declaraciones de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> clase devuelta por la última operación de análisis completo en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase y recuperarla del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método.

2. Rellene o actualice la lista de tipos.

     El contenido de la lista de tipos puede actualizarse cuando el origen ha cambiado o si ha elegido cambiar el estilo de texto de los tipos en función de la posición del símbolo de intercalación actual. Tenga en cuenta que esta posición se pasa al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método.

3. Determine el tipo que se va a seleccionar en la lista de tipos basándose en la posición del símbolo de intercalación actual.

     Puede buscar en las declaraciones que se obtuvieron en el paso 1 para buscar el tipo que incluye la posición actual del símbolo de intercalación y, a continuación, buscar en la lista de tipos de ese tipo para determinar su índice en la lista de tipos.

4. Rellene o actualice la lista de miembros basándose en el tipo seleccionado.

     La lista de miembros refleja lo que se muestra actualmente en la lista desplegable de **miembros** . Es posible que sea necesario actualizar el contenido de la lista de miembros si el origen ha cambiado o si solo se muestran los miembros del tipo seleccionado y ha cambiado el tipo seleccionado. Si opta por Mostrar todos los miembros del archivo de código fuente, el estilo de texto de cada miembro de la lista debe actualizarse si el tipo seleccionado actualmente ha cambiado.

5. Determine el miembro que desea seleccionar en la lista de miembros basándose en la posición actual del símbolo de intercalación.

     Busque en las declaraciones que se obtuvieron en el paso 1 para el miembro que contiene la posición del símbolo de intercalación actual y, a continuación, busque en la lista de miembros de ese miembro para determinar su índice en la lista de miembros.

6. Devuelve `true` si se han realizado cambios en las listas o en las selecciones de cualquier lista.
