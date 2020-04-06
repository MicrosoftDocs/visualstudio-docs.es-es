---
title: Soporte para la barra de navegación en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704860"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Compatibilidad con la barra de navegación en un servicio de lenguaje heredado
La barra de navegación en la parte superior de la vista del editor muestra los tipos y miembros del archivo. Los tipos se muestran en el menú desplegable izquierdo y los miembros se muestran en el menú desplegable derecho. Cuando el usuario selecciona un tipo, el intercalador se coloca en la primera línea del tipo. Cuando el usuario selecciona un miembro, el intercalador se coloca en la definición del miembro. Los cuadros desplegables se actualizan para reflejar la ubicación actual del intercalador.

## <a name="displaying-and-updating-the-navigation-bar"></a>Visualización y actualización de la barra de navegación
 Para admitir la barra de navegación, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> debe derivar <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> una clase de la clase e implementar el método. Cuando el servicio de lenguaje recibe <xref:Microsoft.VisualStudio.Package.LanguageService> una ventana <xref:Microsoft.VisualStudio.Package.CodeWindowManager>de código, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> la clase base crea una instancia de , que contiene el objeto que representa la ventana de código. A <xref:Microsoft.VisualStudio.Package.CodeWindowManager> continuación, se <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> le da un nuevo objeto al objeto. El <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> método obtiene <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> un objeto. Si devuelve una instancia <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> de <xref:Microsoft.VisualStudio.Package.CodeWindowManager> la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> clase, el método llama al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> método [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para rellenar las listas internas y pasa el objeto al administrador de barras desplegables. El administrador de barras desplegables, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> a su <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> vez, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> llama al método del objeto para establecer el objeto que contiene las dos barras desplegables.

 Cuando el intercalador <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> se <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> mueve, el método llama al método. El <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> método base <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> llama <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> al método de la clase para actualizar el estado de la barra de navegación. Se pasa un <xref:Microsoft.VisualStudio.Package.DropDownMember> conjunto de objetos a este método. Cada objeto representa una entrada en la lista desplegable.

## <a name="the-contents-of-the-navigation-bar"></a>El contenido de la barra de navegación
 La barra de navegación normalmente contiene una lista de tipos y una lista de miembros. La lista de tipos incluye todos los tipos disponibles en el archivo de origen actual. Los nombres de tipo incluyen la información completa del espacio de nombres. A continuación se muestra un ejemplo de código de C- con dos tipos:

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

 Se mostrará `TestLanguagePackage.TestLanguageService` la `TestLanguagePackage.TestLanguageService.Tokens`lista de tipos y .

 La lista de miembros muestra los miembros disponibles del tipo seleccionado en la lista de tipos. Mediante el ejemplo de `TestLanguagePackage.TestLanguageService` código anterior, si es el tipo seleccionado, la lista de miembros contendría los miembros privados `tokens` y `serviceName`. No se `Token` visualiza la estructura interna.

 Puede implementar la lista de miembros para que el nombre de un miembro sea negrita cuando el intercalador se coloca dentro de él. Los miembros también se pueden mostrar en texto atenuado, lo que indica que no están dentro del ámbito donde el intercalador está colocado actualmente.

## <a name="enabling-support-for-the-navigation-bar"></a>Habilitación de la compatibilidad con la barra de navegación
 Para habilitar la compatibilidad con la `ShowDropdownBarOption` barra de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> navegación, debe establecer el parámetro del atributo en `true`. Este parámetro establece la propiedad <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Para admitir la barra de <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> navegación, <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> debe implementar <xref:Microsoft.VisualStudio.Package.LanguageService> el objeto en el método de la clase.

 En la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> implementación del <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> método, si `true`la propiedad <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> está establecida en , puede devolver un objeto. Si no devuelve el objeto, no se muestra la barra de navegación.

 La opción para mostrar la barra de navegación puede ser establecida por el usuario, por lo que es posible que este control se restablezca mientras la vista del editor está abierta. El usuario debe cerrar y volver a abrir la ventana del editor antes de que se realice el cambio.

## <a name="implementing-support-for-the-navigation-bar"></a>Implementación de soporte para la barra de navegación
 El <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método toma dos listas (una para cada lista desplegable) y dos valores que representan la selección actual en cada lista. Las listas y los valores de selección <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> se pueden `true` actualizar, en cuyo caso el método debe volver para indicar que las listas han cambiado.

 A medida que la selección cambia en la lista desplegable de tipos, la lista de miembros debe actualizarse para reflejar el nuevo tipo. Lo que se muestra en la lista de miembros puede ser:

- La lista de miembros para el tipo actual.

- Todos los miembros disponibles en el archivo de origen, pero con todos los miembros que no están en el tipo actual mostrados en texto atenuado. El usuario todavía puede seleccionar los miembros atenuados, por lo que se pueden utilizar para una navegación rápida, pero el color indica que no forman parte del tipo seleccionado actualmente.

  Una implementación <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> del método normalmente realiza los pasos siguientes:

1. Obtenga una lista de las declaraciones actuales para el archivo de origen.

     Hay varias maneras de rellenar las listas. Un enfoque consiste en crear un método <xref:Microsoft.VisualStudio.Package.LanguageService> personalizado en <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> la versión de la clase que llama al método con un motivo de análisis personalizado que devuelve una lista de todas las declaraciones. Otro enfoque podría ser <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> llamar al <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> método directamente desde el método con el motivo de análisis personalizado. Un tercer enfoque podría ser almacenar <xref:Microsoft.VisualStudio.Package.AuthoringScope> en caché las declaraciones de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase devuelta <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> por la última operación de análisis completo de la clase y recuperarla del método.

2. Rellene o actualice la lista de tipos.

     El contenido de la lista de tipos puede actualizarse cuando el origen ha cambiado o si ha elegido cambiar el estilo de texto de los tipos en función de la posición actual del intercalador. Tenga en cuenta que <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> esta posición se pasa al método.

3. Determine el tipo que desea seleccionar en la lista de tipos en función de la posición actual del intercalador.

     Puede buscar las declaraciones que se obtuvieron en el paso 1 para buscar el tipo que encierra la posición del intercalador actual y, a continuación, buscar en la lista de tipos de ese tipo para determinar su índice en la lista de tipos.

4. Rellene o actualice la lista de miembros en función del tipo seleccionado.

     La lista de miembros refleja lo que se muestra actualmente en el menú desplegable **Miembros.** Es posible que sea necesario actualizar el contenido de la lista de miembros si el origen ha cambiado o si solo se muestran los miembros del tipo seleccionado y el tipo seleccionado ha cambiado. Si decide mostrar todos los miembros en el archivo de origen, el estilo de texto de cada miembro de la lista debe actualizarse si el tipo seleccionado actualmente ha cambiado.

5. Determine el miembro que desea seleccionar en la lista de miembros en función de la posición actual del intercalador.

     Busque las declaraciones que se obtuvieron en el paso 1 para el miembro que contiene la posición de intercalación actual y, a continuación, busque en la lista de miembros ese miembro para determinar su índice en la lista de miembros.

6. Devuelve `true` si se han realizado cambios en las listas o en las selecciones de cualquiera de las listas.
