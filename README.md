# Website Font Changer
Have you ever wanted to just enlarge the font because the text is either too small or too big? Introducing Website Font Changer! Simply drag the slider and watch the magic begin! Wanna change a different element? Press the "p" button and type the element tag name to have the script change accordingly.  

### Bookmarklet
```
javascript:(
    window.onload = function(){
        let slider = document.createElement("input");
        let sliderBox = document.createElement("div");
        let textBox = document.createElement("button");
        let element = "p";
        let selectStatus = false;
        
        slider.type = "range";
        slider.min = 0;
        slider.max = 100;
        slider.value = 50;

        textBox.textContent = element;
        textBox.style.marginTop = "5px";
        textBox.style.boxShadow = "3px 3px 7px rgba(0, 0, 0, 0.6)";
        
        slider.style.position = "fixed";
        sliderBox.style.position = "fixed";
        sliderBox.style.display = "inline-block";

        slider.style.top = "10px";
        sliderBox.style.top = "10px";
        slider.style.right = "10px";
        sliderBox.style.right = "10px";
        textBox.style.transform = "translateY(1300%)"

        slider.style.transform = "rotate(90deg) translateX(100%)";
        slider.style.transformOrigin = "top right";
        
        slider.style.width = "250px";
        sliderBox.style.height = "250px";                                                                 
        sliderBox.style.width = "15px";
        sliderBox.style.border = "3px solid white";
        sliderBox.style.borderRadius = "5px";
        sliderBox.style.backgroundColor = "white";
        sliderBox.style.boxShadow = "3px 3px 7px rgba(0, 0, 0, 0.6)";

        sliderBox.style.alignItems = "center";
        sliderBox.style.justifyItems = "center";

        sliderBox.appendChild(slider);
        sliderBox.appendChild(textBox);
        document.body.appendChild(sliderBox);

        let text = document.getElementsByTagName(element);
        let ogFontList = [];
        function updateList(){
            ogFontList = [];
            text = document.getElementsByTagName(element);
            for(let i = 0; i < text.length; i++){
                ogFontList[i] = window.getComputedStyle(text[i]).fontSize;
            }
        }

        updateList();
        function changeFont(change){
            for(let i = 0; i < text.length; i++){
                text[i].style.fontSize = parseInt(ogFontList[i]) + change + "px";
            }


        }
        slider.addEventListener("input", function(){
            changeFont(parseInt(slider.value) - 50);
        });

        textBox.addEventListener("click", function(){
            element = prompt("What element name? Don't make mistakes, otherwise an error will occur!");
            if(element != null || element != ""){
                textBox.textContent = element;
            }
            updateList();
        });
        
        
    
    
    }
    

)();
```

