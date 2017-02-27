---
title: "Ventana de comandos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.CommandWindow"
helpviewer_keywords: 
  - "Modo Comando de la Ventana Comandos"
  - "Comandos (ventana)"
  - "IDE de la ventana Comandos"
  - "IDE, Comandos (ventana)"
  - "Modo Marcar de la ventana Comandos"
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Ventana de comandos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ventana **Comando** se utiliza para ejecutar comandos o alias directamente en el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Puede ejecutar los comandos de los menús y los que no aparecen en ningún menú.  Para mostrar la ventana **Comando**, seleccione **Otras ventanas** en el menú **Ver** y elija **Ventana Comando**.  
  
## Mostrar los valores de las variables  
 Para comprobar el valor de una variable `varA`, utilice el [Imprimir \(Comando\)](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 El signo de interrogación \(?\) es un alias de `Debug.Print`, por lo que este comando también se puede escribir como:  
  
```  
>? varA  
```  
  
 Ambas versiones de este comando devolverán el valor de la variable `varA`.  
  
## Escribir comandos  
 El signo de mayor que \(`>`\) aparece en el borde izquierdo de la ventana Comando como símbolo que solicita la introducción de nuevas líneas.  Use las teclas de dirección FLECHA ARRIBA y FLECHA ABAJO para desplazarse por los comandos ejecutados previamente.  
  
|Tarea|Soluciones|Ejemplo|  
|-----------|----------------|-------------|  
|Evaluar una expresión.|Escriba una interrogación de cierre \(`?`\) delante de la expresión.|`? myvar`|  
|Cambiar a una ventana Inmediato.|Escriba `immed` en la ventana sin el mayor que signo \(\>\)|`immed`|  
|Volver a la ventana Comando desde una ventana Inmediato.|Escriba `cmd` en la ventana.|`>cmd`|  
  
 Los siguientes métodos abreviados le ayudarán a navegar en el modo Comando.  
  
|Acción|Ubicación del cursor|Combinación de teclas|  
|------------|--------------------------|---------------------------|  
|Recorrer en ciclo la lista de comandos especificados anteriormente|Línea de entrada|FLECHA & ABAJO OF PANT\/PET ARRIBA|  
|Desplazarse hacia arriba en la ventana.|Contenido de la ventana Comandos|CTRL\+FLECHA ARRIBA|  
|Desplazarse hacia abajo en la ventana.|Contenido de la ventana Comandos|FLECHA ABAJO O CRTL \+ FLECHA ABAJO|  
  
> [!TIP]
>  Puede copiar la totalidad o parte del comando anterior en la línea de entrada; para ello, vaya hasta él, resáltelo todo o sólo una parte y, después, presione ENTRAR.  
  
## Modo Marcar  
 Cuando se hace clic en cualquier línea anterior en la **Comando** ventana, se cambia automáticamente al modo Marcar.  Esto le permite seleccionar, editar y copiar el texto de comandos anteriores tal como lo haría en cualquier editor de texto, y pegarlo en la línea actual.  
  
## El signo igual \(\=\)  
 La ventana utilizada para escribir el comando `EvaluateStatement` determina si un signo igual \(\=\) se interpreta como un operador de comparación o como un operador de asignación.  
  
 En la ventana **Comandos**, un signo igual \(\=\) se interpreta como un operador de comparación.  No se puede utilizar operadores de asignación en la ventana **Comando**.  Así, por ejemplo, si los valores de las variables `varA` y `varB` son diferentes, el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 devolverá un valor de `False`.  
  
 En la ventana **Inmediato**, por el contrario, un signo igual \(\=\) se interpreta como un operador de asignación.  Así, por ejemplo, el comando  
  
```  
>Debug.EvaluateStatement(varA=varB)  
```  
  
 asignará a la variable `varA` el valor de la variable `varB`.  
  
## Parámetros, modificadores y valores  
 Algunos comandos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tienen argumentos, modificadores y valores obligatorios y opcionales.  Al utilizar estos comandos, se aplican determinadas reglas.  A continuación se muestra un ejemplo de un comando enriquecido, con el fin de clarificar la terminología.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 En este ejemplo,  
  
-   `Edit.ReplaceInFiles` es el comando  
  
-   `/case` y `/pattern:regex` son modificadores \(precedidos por el carácter barra inclinada \[\/\]\)  
  
-   `regex` es el valor del modificador `/pattern`; el modificador `/case` no tiene ningún valor  
  
-   `var[1-3]+` y `oldpar` son parámetros  
  
    > [!NOTE]
    >  Cualquier comando, parámetro, modificador o valor que contenga espacios debe tener comillas a ambos lados.  
  
 Normalmente, la posición de los modificadores y los parámetros puede intercambiarse libremente en la línea de comandos, con la excepción del comando [Shell](../../ide/reference/shell-command.md), que requiere modificadores y parámetros propios en un orden específico.  
  
 Casi todos los modificadores admitidos por un comando tienen dos formatos: un formato corto \(de un carácter\) y un formato largo.  Varios modificadores de formato corto pueden combinarse en un grupo.  Por ejemplo, `/p /g /m` puede expresarse también como `/pgm`.  
  
 Si varios modificadores de formato corto se combinan en un grupo al que se le da un valor, este valor se aplica a cada modificador.  Por ejemplo, `/pgm:123` equivale a `/p:123 /g:123 /m:123`.  De este modo, si cualquiera de los modificadores del grupo no acepta un valor, se produce un error.  
  
## Carácter de escape  
 El carácter que va a continuación de un carácter de intercalación \(^\) en una línea de comandos se interpreta literalmente y no como carácter de control.  El símbolo de intercalación puede utilizarse para incrustar comillas \("\), espacios, barras diagonales iniciales, símbolos de intercalación o cualquier otro carácter literal en un valor de modificador o parámetro, con la excepción de nombres de modificador.  Por ejemplo,  
  
```  
>Edit.Find ^^t /regex  
```  
  
 Un símbolo de intercalación funciona del mismo modo tanto dentro como fuera de comillas.  Si el último carácter de la línea es un símbolo de intercalación, éste se omite.  El ejemplo mostrado aquí muestra cómo buscar el modelo “^t”.  
  
## Se de uso con nombres de ruta con espacios  
 Si, por ejemplo, desea abrir un archivo con la ruta que contiene espacios, debe colocar comillas dobles alrededor de ruta o del segmento de trazado que contiene espacios: C:\\" Archivos programa” o “C:\\Program archivos”.  
  
## Vea también  
 [Alias de comandos de Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Comandos de Visual Studio](../../ide/reference/visual-studio-commands.md)