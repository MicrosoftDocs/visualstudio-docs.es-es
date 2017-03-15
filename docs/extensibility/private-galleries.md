---
title: "Galer&#237;as privadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Galerías VSIX, privadas"
  - "galerías privadas, VSIX"
ms.assetid: b6b3dee7-91c5-4556-9f69-0d56b675e83b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Galer&#237;as privadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede compartir los controles, plantillas y herramientas de desarrollo publicándolos en un *Galería privada* en la intranet de su organización, como sigue:  
  
-   Crear un Atom fuente RSS \(\) en una ubicación central \(repositorio\) configurada de forma adecuada en la intranet. Para obtener más información, consulta [Cómo: crear un subcomponente de fuente para una galería privada](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).  
  
-   Distribuir un archivo .pkgdef que describe la Galería privada. Se recomienda esta configuración para los administradores que desean conectarse una galería privada en varios equipos al mismo tiempo.  
  
## Agregar una galería privada a extensiones y actualizaciones de Visual Studio  
 Cuando una galería privada está disponible, puede agregarlo a **extensiones y actualizaciones** en Visual Studio.  
  
 ![Cuadro de diálogo para agregar del Administrador de extensiones](../extensibility/media/em_adddialog.png "EM\_AddDialog")  
  
#### Para agregar una galería privada a extensiones y actualizaciones  
  
1.  En la barra de menús, elija **Herramientas**, **Opciones**.  
  
2.  En el **entorno** nodo, seleccione **extensiones y actualizaciones**.  
  
3.  Elija el botón de **Agregar**.  
  
4.  En el **nombre** introduzca un nombre para la Galería privada, por ejemplo, `My Gallery`.  
  
5.  En el **URL** escriba la dirección URL de la fuente Atom o un sitio de SharePoint que hospeda la Galería privada.  
  
    1.  Si el host es una fuente Atom que se conecta a la Galería privada, la dirección URL parecerá a ésta: http:\/\/www.mywebsite\/mygallery\/atom.xml.  Esta dirección URL puede hacer referencia a un archivo o una ruta de acceso de red.  
  
    2.  Si el host es un sitio de SharePoint, la dirección URL parecería ésta: http:\/\/mysharepoint\/sites\/mygallery\/forms\/AllItems.aspx.  
  
### Administrar galerías privadas  
 Un administrador puede disponer de una galería privada en varios equipos al mismo tiempo, modifique el registro del sistema en cada equipo. Para ello, cree un archivo .pkgdef que describe las nuevas claves del registro y sus valores.  El formato de este archivo es el siguiente.  
  
```  
[$RootPath$\ExtensionManager\Repositories\{UniqueGUID}]  
@={URI}  (REG_SZ)  
Disabled=0 | 1 (DWORD)  
Priority=0 (highest priority) … MaxInt (lowest priority) (DWORD) (uint)  
Protocol=VSGallery|Atom|Sharepoint (REG_SZ)  
DisplayName={DisplayName} (REG_SZ)  
DisplayNameResourceID={ID} (REG_SZ)  
DisplayNamePackageGuid={GUID} (REG_SZ)  
  
```  
  
 Para obtener más información, consulta [Cómo: administrar una galería privada mediante la configuración del registro](../extensibility/how-to-manage-a-private-gallery-by-using-registry-settings.md).  
  
## Instalar extensiones desde una galería privada  
 Puede buscar e instalar extensiones de Visual Studio desde una galería privada de **extensiones y actualizaciones**. Los pasos siguientes usan una galería privada denominada `My Gallery`.  
  
 ![Administrador de extensiones instalando una galería privada](../extensibility/media/em_.png "EM\_")  
  
#### Para buscar e instalar extensiones desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **extensiones en línea**, y, a continuación, seleccione **Mi galería**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija la **descargar** botón.  
  
## Actualizar extensiones desde una galería privada  
 Se publican nuevas versiones de extensiones de Visual Studio en la Galería privada, puede actualizar las extensiones que haya instalado. Los pasos siguientes usan una galería privada denominada `My Repository`.  
  
 ![Actualización de la galería privada del Administrador de extensiones](../extensibility/media/em_update.png "EM\_Update")  
  
#### Para actualizar una extensión instalada desde una galería privada  
  
1.  En la barra de menús, elija **Herramientas**, **Extensiones y actualizaciones**.  
  
2.  En el panel izquierdo, seleccione **actualizaciones**, y, a continuación, seleccione **Mi repositorio**.  
  
3.  En el panel derecho, seleccione una extensión y, a continuación, elija la **actualización** botón.  
  
## Vea también  
 [Buscar y usar extensiones de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)   
 [Envío de extensiones de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)