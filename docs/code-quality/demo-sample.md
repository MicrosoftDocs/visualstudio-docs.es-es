---
title: "Ejemplo de demostraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "análisis de código, ejemplos"
  - "ejemplo de demostración [Visual Studio ALM]"
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# Ejemplo de demostraci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En los procedimientos siguientes se muestran cómo se crea el ejemplo de [Tutorial: Analizar código de C\/C\+\+ en previsión de defectos](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md).  Los procedimientos crean:  
  
-   Una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] denominada CppDemo.  
  
-   Un proyecto de biblioteca estática denominado CodeDefects.  
  
-   Un proyecto de biblioteca estática denominado Annotations.  
  
 Los procedimientos también proporcionan el código del encabezado y los archivos .cpp de las bibliotecas estáticas.  
  
### Crear la solución CppDemo y el proyecto CodeDefects  
  
1.  Haga clic en **Archivo**, elija **Nuevo** y, a continuación, haga clic en **Nuevo proyecto**.  
  
2.  En la lista de árbol **Tipos de proyecto**, si Visual C\+\+ no es el lenguaje predeterminado en VS, expanda **Otros lenguajes**.  
  
3.  Expanda **Visual C\+\+** y, a continuación, haga clic en **General**.  
  
4.  En **Plantillas**, haga clic en **Proyecto vacío**.  
  
5.  En el cuadro de texto **Nombre**, escriba **CodeDefects**.  
  
6.  Active la casilla **Crear directorio para la solución**.  
  
7.  En el cuadro de texto **Nombre de la solución**, escriba **CppDemo**.  
  
### Configurar el proyecto CodeDefects como una biblioteca estática  
  
1.  En el Explorador de soluciones, haga clic con el botón secundario en **CodeDefects** y, a continuación, haga clic en **Propiedades**.  
  
2.  Expanda **Propiedades de configuración** y, a continuación, haga clic en **General**.  
  
3.  En la lista **General**, seleccione el texto de la columna situada junto a **Extensión de destino** y, a continuación, escriba **.lib**.  
  
4.  En **Valores predeterminados del proyecto**, haga clic en la columna situada junto a **Tipo de configuración** y, a continuación, haga clic en **Biblioteca estática \(.lib\)**.  
  
### Agregar el encabezado y el archivo de origen al proyecto CodeDefects  
  
1.  En el Explorador de soluciones, expanda **CodeDefects**, haga clic con el botón secundario en **Archivos de encabezado**, haga clic en **Agregar** y, a continuación, haga clic en **Nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y, a continuación, haga clic en **Archivo de encabezado \(.h\)**.  
  
3.  En el cuadro **Nombre**, escriba **Bug.cpp** y, a continuación, haga clic en **Agregar**.  
  
4.  Copie y pegue el siguiente código en el archivo **Bug.cpp** en el editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  En el Explorador de soluciones, haga clic con el botón secundario en **Archivos de origen**, seleccione **Nuevo** y, a continuación, haga clic en **Nuevo elemento**.  
  
6.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo C\+\+ \(.cpp\)**.  
  
7.  En el cuadro **Nombre**, escriba **Bug.cpp** y, a continuación, haga clic en **Agregar**.  
  
8.  Copie y pegue el siguiente código en el archivo Bug.h del editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Haga clic en el menú **Archivo** y, a continuación, en **Guardar todo**.  
  
### Agregar el proyecto Annotations y configurarlo como una biblioteca estática  
  
1.  En el Explorador de soluciones, haga clic en **CppDemo**, elija **Agregar** y, a continuación, haga clic en **Nuevo proyecto**.  
  
2.  En el cuadro de diálogo **Agregar nuevo proyecto**, expanda Visual C\+\+, haga clic en **General** y, a continuación, en **Proyecto vacío**.  
  
3.  En el cuadro de texto **Nombre**, escriba **Annotations** y, a continuación, haga clic en **Agregar**.  
  
4.  En el Explorador de soluciones, haga clic con el botón secundario en **Annotations** y, a continuación, haga clic en **Propiedades**.  
  
5.  Expanda **Propiedades de configuración** y, a continuación, haga clic en **General**.  
  
6.  En la lista **General**, seleccione el texto de la columna situada junto a **Extensión de destino** y, a continuación, escriba **.lib**.  
  
7.  En **Valores predeterminados del proyecto**, haga clic en la columna situada junto a **Tipo de configuración** y, a continuación, haga clic en **Biblioteca estática \(.lib\)**.  
  
### Agregar el archivo de encabezado y el archivo de origen al proyecto Annotations  
  
1.  En el Explorador de soluciones, expanda **Annotations**, haga clic con el botón secundario en **Archivos de encabezado**, haga clic en **Agregar** y, a continuación, haga clic en **Nuevo elemento**.  
  
2.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Archivo de encabezado \(.h\)**.  
  
3.  En el cuadro **Nombre**, escriba **annotations.h** y, a continuación, haga clic en **Agregar**.  
  
4.  Copie y pegue el siguiente código en el archivo **annotations.h** del editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  En el Explorador de soluciones, haga clic con el botón secundario en **Archivos de origen**, seleccione **Nuevo** y, a continuación, haga clic en **Nuevo elemento**.  
  
6.  En el cuadro de diálogo **Agregar nuevo elemento**, haga clic en **Código** y, a continuación, haga clic en **Archivo C\+\+ \(.cpp\)**.  
  
7.  En el cuadro **Nombre**, escriba **annotations.cpp** y haga clic en **Agregar**.  
  
8.  Copie y pegue el siguiente código en el archivo **annotations.cpp** del editor de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Haga clic en el menú **Archivo** y, a continuación, en **Guardar todo**.