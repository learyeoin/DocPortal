---
title: /Customisation
position: 1.5
type: css
description: Customise your form
author: Eóin O'Leary
right_code: |



  ![Default](http://localhost:4000/images/standalone.png){:class="img-responsive"}
  {: title="Response" }

  
---


 

This below CSS can be customised and sent back to our team to add to your account.
{: .info }




  ~~~ css  
h1, h2, h3, h4 {
    font-family: "Anton", Arial, Helvetica, sans-serif;
}
 
h1 {
    color: #dddddd;
}
 
h2 {
    font-weight: normal;
}
 
h3,h4 {
    color: navy;
}
a {
    color: navy;
}
 
#myriadCashierContainer {
    border-radius: 0.6em;
    background-color: white;
}
 
 
label {
    color: darkgray;
}
 
span:hover label {
    color: navy;
}
 
input:hover, input:focus, .radio label:hover{
    box-shadow: navy 0 0 4px;
}
 
input,select {
    color: slategray;
    border: 0;
    border: 1px solid lightgray;
    border-radius: 0.4em;
    background: none;
    background-image: url(../img/FFFFFF-0.5.png);
}
 
.radio label{
    background-color: papayawhip;
    color: navy;   
}
 
.radio input[type=radio]:checked+label{
    color: white;
    background-color: navy;
}
 
 
.col21>p{
    color: gray;
}
 
small {
    color: lightgray;
}
/* Pay Button */
button {
    background-color: navy;
    border-color:gray;
    color: white;
}
 
button:hover {
    box-shadow: navy 0 0 4px;
}
 
button.main {
    background-color: crimson;
}
 
div.myriadpayments {
    color: navy;
}
 
span.myriadCardNumber {
    background-color: rgba(0, 0, 0, 0);
}
 
 
::-webkit-input-placeholder {
    color: #ccc;
}
 
:-moz-placeholder {
    color: #ccc;
}
 
:-ms-input-placeholder {
    color: #ccc;
}
 
 
input.touched:invalid,select.touched:invalid {
    border-color: red;
    box-shadow: red 0 0 4px;
}
 
input.touched:valid,select.touched:valid {
    border-color: green;
    box-shadow: none 0 0 0;
}
 
input[type=checkbox]:checked+label::before {
    color: white;
    background-color: navy;   
}
 
input[type=checkbox]+label::before {
    border-color:navy;
    color: navy;
    background-color: papayawhip;
    border-radius: 0.4em;
}
 
label a{
    color: navy;
}
/* Cancel Button */
.myriadSubmit button[type="reset"] {
    background-color: papayawhip;
    border-color: gray;
    color: navy;
}
 
.pair-left {
    border-radius: 0.5em 0 0 0.5em;
    border-right: 0 none;
}
 
.pair-right {
    border-radius: 0 0.5em 0.5em 0;
    border-left: 1px dotted gray;
}
 
 
.message {
    background-color: navy;
    border-bottom: 1px solid navy;
    border-radius: 0.5em;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
}
 
.token {
    color: white;
}
 
input.error {
    border-color:red;
}
 
#myriadMessage .error {
    color: red;
    border: none;
}
 
#myriadMessage .error.field {
    color: gray;
    font-size: 0.6em;
    border: 0;
}
 
#myriadMessage {
    background-color: white;
    color: navy;
    box-shadow: navy 1px 1px 8px;
    border-radius: 0.5em;
}
 
#myriadPopup iframe {
    border: 0;
    background-color: white;
}
 
.result {
    font-family: "Anton", sans-serif;
    font-size: 2em;
    background-color: white;
    border-radius: 0.5em;
    line-height: 1em;
}
 
.success {
    color: white;
    background-color: red;
}
 
.failure {
    color: white;
    background-color: red;
}
 
.cancel {
    color: white;
    background-color: orange;
}
 
.paymentMethod {
    line-height: 1em;
    background-color: navy;
    text-indent: 0;
    color: white;
    border-radius: 0.5em;
}
 
.paymentMethod:hover {
    background-color: #00adad;
    box-shadow: #00adad 0 0 4px;
}
  ~~~

{: title="CSS" }
