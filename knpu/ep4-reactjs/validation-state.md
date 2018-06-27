# Validation State

Coming soon...

I want to talk a little bit about validation, um, because obviously there's going to ultimately, when we smith the server need some validation on our fields here. They're actually three different types of validation. You have service I validation, which we absolutely will need to make sure people don't submit ridiculous data. Client side validation, which is a 

and also client side validation in html five validation those last two times or just a nice to have so you can totally skip them if you want to. But if you want to have a slightly better Ui, Ben, they're a good thing to add. Each team of five validation is really easy but not very flexible and most of the time it's things like adding the required attributes. So this prevents our form from being submitted empty already. I want to add a little bit of client side validation that makes sure that we can't submit this with a negative number right now. That's totally allowed and there's no reason to even let the user submit that. By the way, the fact that we have a, uh, input type equals number field already prevents us from entering words into the fields. That's another type of html five validation. All right, so how do we do this? Well, the behavior we want is that when we actually submit the form, that's what we want to show the validation message. So when we submit the form, that is when our handle form submit a scholar. Perfect. Right here, we can add an if statement that says if wanted to input that value is less than or equal to zero, we also won't allow zero, then I'll put it to do here. This is where we want to print some validation error. 

Okay, 

well we also want to not submit and not clear the form, which we can easily do by just returning from the function. So we don't hit our code below. Awesome. So let's double check and make sure this works at least so far. Maybe put a negative 10 and select an item. Yep. You can see it as not clearing the form. So it looks like that's probably working. All right. So question is how do we print some validation message here dynamically? Well, this exhibit is exactly the purpose of state. What I mean is 

if we had some validation error message states than we could change the state here and use that state down and render. Then whenever the state changed, it would rerender this components and it print out the new message. This is exactly what state is for, but right now all of our state lives up in rep log app and I've told you so far, that's what I want you to do. That enabled all of our other components to be dumb stateless components and that's a distinction. We want to have smart state full components and dumb stateless components, but in reality there are some real use cases for your dumb components like Rep la Creator to have state and this is one of them having a validation error. Message state has nothing to do with our business logic. I want to keep our business logic state up high and rep log APP. This is state related entirely to the user interface and it's the user interface of this components. So I want your dumb components to at first, not have state, but if you do need states to power the user interface of that component, then it's okay. But if it's state that's important to your business, I want you to put it in your top level component. So here we go. We're going to add state, which means that we're always going to go into our constructor and initialize it. This dot state equals, and we'll call it quantity input error, and we'll initialize it to an empty quotes. 

Now down below, very simply, instead of this to do, we can say this dot set state almost that quantity 

input error too. 

Please enter a value greater 

and zero. 

And then also down here, after a successful form submit, we're going to want to change that back to empty quotes. So I'll copy the set state line and we'll set this back to empty quotes because we want to make sure that input air actually disappears. 

All right, perfect. Finally, down and render. Let's use this. And as always we're going to destructure the variable out first. So we'll say quantity input error equals this dot state. And there's two things I want to do here. I want to first actually want to make my form element actually appear red. And then I'm also going to print the air message. So to make it appear red, what we need to do is, because I'm using bootstrap, we need to add a form class here called has dash air only if we have in that quantity input. Error State is not empty, but of course we always want this form dash group class. So what we can do here is use javascript to concatenate those classes together. We're actually is even a cooler way, so first. So I'll copy the form dash group and I'm going to change this. Use javascript. Then I'll use the tick format because then we can just start typing 

normal 

strings in here. And then whenever we need a variable, we'll say dollar sign, open curly brace. And here we can say quantity input error that if we have that, we'll add the has dash air class. Otherwise we'll add nothing. So javascript string interpolation inside of javascript. I know it's a little crazy. Then finally, to actually print the message, we'll go down here after the inputs and here once again we want to print a message but only print that message if quantity input error is set. So once again it might have been thinking that it makes sense to do something like wanted to input error, 

then print the quantity of air else, print empty quotes and that's good. The problem is it's more complicated than that because I want to actually surround my quantity input error in a span tag so it gets kind of ugly here because you're like, okay, well what I really want here is actually a span tag. Then I'll print quantity of air, so that's fine, but there's a weird shortcut syntax we can use whenever you want to print a string. Um, if it's set, it looks like this quantity input, air and, and then I'm going to add my jsx here, which is going to be a span with health block. And then I'll print quantity input error, my closing span tag, and then I need my closing javascript. Cool. Before we talk about that, let's try it. 

Move over. 

Make sure the page is fully refreshed 

and let's select an item negative 10 and enter, and there it is. We have the red highlight things to the class and there's our message. It's ugly, but we'll fix the message in a second. So in javascript it's a little bit weird because when you use the syntax, which is normally using, if statements, if the first thing is false, it just returns false. But if the first thing is true, it actually returns. The second thing here, which is going to be the react element object. So that's again one of those fancy syntaxes, which can be confusing at first if you like it, use it. If you don't like it, don't worry about it. Now finally it's make this look a little bit less ugly. I'm actually going to go back into our logs elements and down here we can just surround this with a little bit of bootstrap markup, but that inside of a column in a row that's going to give that just a little bit more structure. So when we go and refresh this time and fill in a value, then I'll also go into rep creator and I'll go up to the form element and I'm actually going to take off the form in line. It's just gonna. Make the whole form flow a little bit better now. So over here, do a full big refresh. Cool. You can see this breaks things onto their own lines, but because of our column, it's actually a little bit thinner. Design details are important and when we submit yes, that looks much nicer. So next, let's talk about a completely different way to handle forums called control inputs.