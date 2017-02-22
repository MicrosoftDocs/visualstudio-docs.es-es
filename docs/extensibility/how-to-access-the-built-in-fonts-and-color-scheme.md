---
title: "C&#243;mo: obtener acceso a las fuentes integradas y la combinaci&#243;n de colores | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fuentes, acceso integrado"
  - "control de fuente y color [Visual Studio SDK], categorías"
  - "colores, obtener acceso a los esquemas integrados"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# C&#243;mo: obtener acceso a las fuentes integradas y la combinaci&#243;n de colores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El entorno de desarrollo integrado \(IDE\) de Visual Studio tiene una combinación de fuentes y colores que está asociada a la ventana del editor. Puede tener acceso a este esquema a través de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.  
  
 Para utilizar las fuentes integradas y la combinación de colores, un VSPackage debe:  
  
-   Definir una categoría para utilizarla con el servicio de fuentes y colores de forma predeterminada.  
  
-   Registrar la categoría con el servidor de fuentes y colores de forma predeterminada.  
  
-   Notificar el IDE que una ventana específica utiliza los elementos de pantalla integrada y categorías utilizando la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` y `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaces.  
  
 El IDE utiliza la categoría resultante como un identificador de la ventana. Nombre de la categoría que se muestra en el **Mostrar valores para:** cuadro de lista desplegable en el **fuentes y colores** página de propiedades.  
  
### Para definir una categoría con colores y fuentes integradas  
  
1.  Cree un GUID arbitrario.  
  
     Este GUID se utiliza para identificar de forma exclusiva una categoría**.** Esta categoría reutiliza la especificación de colores y fuentes de predeterminado del IDE.  
  
    > [!NOTE]
    >  Al recuperar datos de fuente y color con el <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o de otras interfaces, VSPackages utilizar este GUID para hacer referencia a información integrada.  
  
2.  Nombre de la categoría debe agregarse a una tabla de cadenas dentro del archivo de recursos \(.rc\) de VSPackage, por lo que puede localizarse según sea necesario cuando se muestran en el IDE.  
  
     Para obtener más información, consulta [Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string).  
  
### Para registrar una categoría de uso de colores y fuentes integradas  
  
1.  Construir un tipo especial de entrada de registro de la categoría en la siguiente ubicación:  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< versión de Visual Studio \>*\\FontAndColors\\*\< categoría \>*\]  
  
     *\< categoría \>* es el nombre no traducido de la categoría.  
  
2.  Rellenar el registro para usar las fuentes estándar y la combinación de colores con cuatro valores:  
  
    |Nombre|Tipo|Datos|Descripción|  
    |------------|----------|-----------|-----------------|  
    |Categoría|REG\_SZ|GUID|Un GUID arbitrario que identifica una categoría que contiene el esquema de color y fuente estándar.|  
    |Paquete|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> Este GUID se usa por todos los VSPackages que utilice las configuraciones predeterminadas de color y fuente.|  
    |NameID|REG\_DWORD|Id.|El identificador de recurso de un nombre de categoría localizable de VSPackage.|  
    |ToolWindowPackage|REG\_SZ|GUID|El GUID del paquete VSPackage que implementa el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaz.|  
  
3.  
  
### Para iniciar el uso de colores y fuentes proporcionada por el sistema  
  
1.  Cree una instancia de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaz como parte de la implementación y la inicialización de la ventana.  
  
2.  Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método para obtener una instancia de la `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interfaz correspondiente a la actual <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instancia.  
  
3.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> dos veces.  
  
    -   Llame a la vez con `VSEDITPROPID_ViewGeneral_ColorCategory`como argumento.  
  
    -   Llame a la vez con `VSEDITPROPID_ViewGeneral_FontCategory` como argumento.  
  
     Esto establece y expone los servicios predeterminados, fuentes y colores como una propiedad de la ventana.  
  
## Ejemplo  
 En el ejemplo siguiente se inicia el uso de colores y fuentes integradas.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## Vea también  
 [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md)   
 [Obtención de información de Color para los colores de texto y de fuente](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Obtener acceso a la configuración de Color y fuente almacenado](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Introducción de Color y fuente](../extensibility/font-and-color-overview.md)