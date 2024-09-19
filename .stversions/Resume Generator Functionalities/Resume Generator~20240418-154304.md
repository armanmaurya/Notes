A Resume is very important for students because it tells about the student's personality, experience, skills and Academic Qualification. So we thought we should make a resume generator which will help them to get a resume easily without dealing with any graphics software and Out journey begins.

So first we searched about best available way to provide our service to students and we got to know about html, css, and javascript which can be easily served to any browser irrespective to operating system weather it's Android, Windows, Linux or any other OS, they only have to go to our website and fill the information required to generate a resume and they can just download this resume easily.

So, we discussed about this project and concluded the steps required to complete this projects:-

**Step-1:** We have to design structure of front-end using html which contains textarea for the information to be filled in, a generate resume button used to generate resume and final resume layout which can be downloaded in pdf format.

**Step-2:** Layout should be User-Friendly for to easily navigation

**Step-3:** Generate the resume when generate resume button is clicked.

Now, we got the steps to complete this project so back to **Step-1** we have created a textarea and a label to that textarea, label tells what information needed to be filled in that textarea. We have created many fields like this Such as Name of the student, Contact information, Address, Photo and many other field which is required for the resume.
![](Screenshot_20240124_002910.png)
We have also divided the structure in two segment one which contains Personal Information and Second which contains Professional Information and lastly 'generate resume' button at the bottom As you can see
![](Screenshot_20240124_004238.png)
This doesn't look good and also not user-friendly So, its time for **Step-2**, To make a design user-friendly we have used bootstrap, why? Because bootstrap is a css framework which helps to fast and easily design the html. We started by linking the bootstrap to our html DOM. As you can see the image,
![](Screenshot_20240124_005346.png)
After bootstrap was successfully linked We have divided the Personal Information block and Professional Information Block into two column, adjusted the margin and padding for right alignment of html tags and also beautifying the buttons and textarea for good looking UI (user Interface).  
![](Screenshot_20240124_005957.png)
So out design as completed, now, its time for **Step-3** we have to generate a resume when 'generate resume' button is clicked So this we have used the Javascript, first we have to link the javascript to our html DOM
![](Screenshot_20240124_011840.png)
After Javascript is linked now we are ready to write the function which will run when the button is clicked 
The function is,
```javascript
function generateCV() {
  // console.log("generating CV")

  let nameField = document.getElementById("nameField").value;

  let nameT1 = document.getElementById("nameT1");

  nameT1.innerHTML = nameField;

  // direct

  document.getElementById("nameT2").innerHTML = nameField;

  // contact
  document.getElementById("contactT").innerHTML =
    document.getElementById("contactField").value;

  //  adderess
  document.getElementById("addressT").innerHTML =
    document.getElementById("addressField").value;

  document.getElementById("fbT").innerHTML =
    document.getElementById("fbField").value;

  document.getElementById("instaT").innerHTML =
    document.getElementById("instaField").value;

  document.getElementById("linkedT").innerHTML =
    document.getElementById("linkedField").value;

  document.getElementById("twitterT").innerHTML =
    document.getElementById("twitterField").value;

  // objective
  document.getElementById("objectiveT").innerHTML =
    document.getElementById("objectiveField").value;

  //workexperience

  let wes = document.getElementsByClassName('weField');

  let str = "";



  for (let e of wes) {
    str = str + `<li>${e.value}</li>`;
  }
  document.getElementById("weT").innerHTML = str;


  //acadmaic experience
  let aqs = document.getElementsByClassName('eqField');

  let a_str = "";

  for (let e of aqs) {
    a_str = a_str + `<li>${e.value}</li>`;
  }

  document.getElementById("adT").innerHTML = a_str;

  // code for setting Image
  let file=document.getElementById('imgField').files[0];

  console.log(file);

  let reader= new FileReader();

  reader.readAsDataURL(file);

  console.log(reader.result);

  // set the image to template

 reader.onloadend= function()
 {
  document.getElementById("imgTemplate").src = reader.result;
 }

  document.getElementById("cv-form").style.display = "none";
  document.getElementById("cv-template").style.display = "block";


}

```
So our Step-3 is complete we get the data that was inserted in textarea and generate a resume based on the information provided.
And this resume can also be download in pdf format.