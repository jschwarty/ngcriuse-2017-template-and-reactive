Good afternoon, time to get some answers about forms in Angular...on a cruise ship! Because, what better place to make choices about online data collection than on a boat in the middle of the Bahamas right?
 
I’m Justin Schwartzenberger, also known as Schwarty, 
I author Angular training courses at Lynda.com, and coming soon at Schwarty.com...
And I host and maintain AngularAir, a weekly videocast all about Angular.
 
Okay, enough about me. This is about us...and forms!
 
So, Angular forms. Plural. What is that all about, right? Why do we have two different ways to do forms and which do we choose? 
 
We need some answers so we can get a better understanding of what’s going on here.
 
Well, they say the first step to understanding is acceptance.
 
Let’s accept the fact we have two ways to do forms, and get busy figuring out which we should use.
 
In one of those ways, we bind data models to form fields and let Angular do the heavy lifting
 
and in the other we build out a form representation and attempt to take more control over data changes and validation.
 
At the conceptual level we refer to these as Template-Driven Forms and Reactive Forms.
 
And these are not baked into the core platform. They are available as part of a separate library in the collection of official Angular packages.
 
Angular has one scoped package for forms... @angular/forms
 
But it has two NgModules for forms…
FormsModule and ReactiveFormsModule
 
FormsModule maps to Template-Driven 
 
and ReactiveFormsModule maps to Reactive.
 
And something that we hear a lot about in the comparison of these two is that Template forms give us a way to do formy type stuff all within our markup, similar to how it’s done in AngularJS.
 
And Reactive forms give us a way to react to form changes and validation.
 
But these are not really the best descriptions of the two. 
 
Because we can actually do a lot of form stuff in the markup when using Reactive Forms. 
 
And we can tap into the EventEmitters like valueChanges and use control value accessors and view and content child queries to get a hold of the form controls in Template Forms.
 
So if we have the ability to do a lot of the same stuff in both...why do we have two to choose from?
 
Well, it’s complicated. 
 
No, just kidding...it’s not that complicated.
 
Why don’t we just go through and compare and contrast the two.
 
We’re going to walk through the whole form building process from start to finish for each of these 
 
and see where we can accomplish the same UI and data collection goals with both using either the exact same code or a similar pattern
 
and we’ll discover where we have to do things completely different to pull of the same thing.
 
Loadout
 
So let’s start from the beginning. 
How do we reference them and start using them?
 
Both of them come from the same scoped package, so including @angular/forms as a dependency is the same for both.
 
Now they each have their own NgModule, so early on things start to differ just a bit. But we can import these in at any NgModule level we want in our application, and we can even have both in at the same time.
 
Components
 
Now with the package and NgModule in place we can turn our attention to the form implementation within our components.
 
For both template and reactive we are going to need to provide some way to save and load data, most likely through a service.
 
So the component for each forms type would get a data service.
 
And this service can have a save method that we can call from within an onSubmit method in each form type that takes in the form value represented as a JavaScript object.
 
We’ll take a look at how we can get the same value object from either of the form types when we take a look at the component markup here in a minute.
 
But before we hop over to that let’s cover the form model representation.
 
For Template forms we do not need to do anything here in the component, we could actually just set up stuff in the component markup, but that would probably only be done in cases where we have a new item form that we don’t want to preload with data.
 
Most likely we would need to get a model from the service, so we’d have at least a class field on the component for a data model.
 
And for Reactive forms we build out the form model representation within the component. To do that we use the FormBuilder service from the ReactiveFormsModule, so we inject that in the constructor.
 
Now this is one of the main differences between Template and Reactive.
 
In Reactive we are creating the form model using Angular’s form stuff.
 
In Template, Angular is going to create the form model for us based on what we do in the markup.
 
But this model stuff that we create in Reactive forms is actually the same stuff Angular will create for us in Template forms. 
 
And because of this, Template and Reactive are actually more alike than different.
 
See we tend to get the impression that we can only bind up values in the markup for Template Forms.
 
And we can only wire up to value changes with Reactive Forms.
 
But we can actually do all this stuff for each.
 
Because the underlying form code is the same for each. We just need to know how to get to it.
 
Now before we jump over to the markup, let’s cover one more point here. 
 
With Reactive forms we can do a lot of stuff in the component constructor. Or we could even do it elsewhere, and hand it in to the component.
 
That’s because we are controlling the instantiation of things like FormGroups and FormControls and can start setting up default values, declare validation rules and wire up to value changes on those.
 
With Template Forms we are relying on directives to be processed on the view before we can get access to the FormGroup and FormControl stuff.
 
So let’s mark this down as one of the potential decision makers for Template or Reactive.
 
If we want to wire things up early on we want to use Reactive.
 
(Html)
 
Okay let’s jump into the markup.
 
First, the form element.
 
In the Template one we don’t need to do anything on form tags. The FormsModule has a NgForm directive that handles finding form elements and initializing a FormGroup for them.
 
In the Reactive one we need to bind the FormGroup from the component class to the ReactiveFormsModule FormGroup directive.
 
Both of these result in a FormGroup for the form. 
 
Difference is that in the Reactive approach we created the FormGroup...
 
And in the Template one the NgForm directive created it after Angular processed this component template.
 
Now, another difference between the two here is the way we go about getting a hold of and working with the form model pieces in the markup.
 
The directives that come with the FormsModule for Template forms have an exportAs property in their decorator metadata.
 
So we can make use of template reference variables on the elements that have been processed by those directives to get a hold of the underlying form model pieces.
 
And with Reactive, we’ve already created those form model pieces in the component class, so we can just use them from there.
 
But some of the directives for Reactive also have an exportAs, so we could potentially do the same template reference variable thing there if we wanted too.
 
Now when it comes to form submission, both Template and Reactive forms can use the ngSubmit Output event that is found on the NgForm directive for Template 
and the FormGroup directive for Reactive
 
And if we use the form template reference variable or the form class field we can send the form.value to the submit function in the same fashion for each.
 
And that form.value is going to be that JavaScript object representation of the entire form model.
 
Now, for the form fields.
 
Wiring up html form elements to Angular form stuff involves directives for both Template and Reactive. And they’re different...there’s not much we can do here to use the same code for both.
 
Template forms require us to use the ngModel directive and a name attribute, which will create a formControl for us.
 
And for Reactive, we can either make use of the formControlName directive and set that to the name we gave the form control when we set up the model or we can use the formControl directive to wire up to the actual formControl we already created.
 
Now getting initial data to the form fields is also different for the two.
 
With Template, we need to do that in the markup via the ngModel directive. And we need to do it there because we don’t have any way to get to the underlying formControl until the Template ngModel directive creates it.
 
With Reactive we can do that either in the code when we create the form model, 
or in the markup through a value property binding.
 
So let’s add this to the existing potential decision maker…
 
if we want to wire things up and/or set the initial value early on we want to use Reactive.
 
And while we are taking a look at binding data to the form model, let’s look at what is probably the biggest difference between Template and Reactive.
 
Template actually provides us the opportunity to two-way bind our own data model to the form model via the banana in a box syntax around ngModel...the square bracket and parenthesis.
 
So, for cases where we want to use our own data models, Template is a good fit. And this works for scenarios where we are upgrading an existing AngularJS app to Angular, or we have a data model library that has validation and business logic built into it and we just need to wire that up for data collection.
 
So, we need to add a second potential decision maker…
 
When we want to bring our data model infrastructure to the party, we want to use Template.
 
Now the forms stuff provides a way to organize subsets of form fields through the use of form groups. A form group can contain form controls and other form groups.
 
Making use of those in the markup is similar to the approach for form fields for each form type.
 
For Template we use the NgModelGroup directive and set that to a string that will be the name that we want to use for the group.
 
For Reactive we use the FormGroupName directive and set that to the name we gave to the form group.
 
Or we use the FormGroup directive and set that equal to a form group from the form model we built.
 
So like the form fields, the wire up of these two is a bit different, but from there we end up with the same underlying formGroup type of model.
 
Okay, a few more things here in the markup…
 
When it comes to validation, we could actually make use of validation directives in the same manner for both Template and Reactive.
 
All of the built in validators that the Angular forms package provides have directives that go along with them.
 
So we can use ones like required, pattern, etc on form fields in the same fashion for Template and Reactive.
 
And when we want to display errors, the way we go about getting a handle to the underlying formControl is a bit different for Template and Reactive.
 
With Template we use a template reference variable to get the exportAs of ngModel
 
And with Reactive we get it from our formGroup that we created in the component class.
 
But from there, the check for an error and access to error data is the same for both.
 
So we can call things like hasError off of each of these because the underlying object is the same for both
 
 
So there are a handful of differences... 
 
But, to be honest, it kinda feels like Template is trying to hide some stuff from us. I mean, it feels like we are working with the same form stuff here on each.
 
Even if we feed it our own model, Template is still making the same FormControl and FormGroup stuff for us that we would do with Reactive.
 
And when we ask for the exportAs stuff we get those back.
 
And the validation approach can be the same.
 
And when we check for errors we are calling the same method signatures and properties...because we are working with the same type of objects.
 
So, really, the role of Template Forms here is to provide a layer of directives that will do the form model instantiation for us.
 
Well, what about Reactive. What is it trying to hide?
 
Not much, but it too is providing a layer of directives...difference being that its directives just need to broker the connection of the elements to the form model we’ve already instantiated.
 
So...after these layers, everything is the same? Really?
 
Really, really.
 
Check it out. Here’s the NgModules source code for Template and Reactive…
 
Both of them just declare and export a small set of unique directives for each.
 
And oh, hey...we see you InternalFormsSharedModule!
 
That NgModule contains all that similar under the hood stuff. 
 
All of the forms models and control value accessors and validators and validator directives are in there and are used by both the FormsModule and ReactiveFormsModule.
 
What does this all mean? Is this madness? Are we flipping the whole forms stuff upside down and looking at it in a new light?
 
Maybe...just maybe.
 
Let’s see what kind of controlled chaos we can pull off.
 
So custom validator directives. Can we write those one way and use them for both Template and Reactive?
 
Check this out…
 
We can create a custom validator directive that adds itself to the NG_VALIDATORS list 
 
And that directive can have a validate method in there that will get handed a control.
 
And when we put that directive on a form field that is wired up either via Template or Reactive…
 
It’s going to receive the same type of underlying form control model from each!
 
So it works for both.
 
And, I know, you’re probably thinking “Okay Mr SchwartyPants, where’s the brilliance in that...that’s an easy one”
 
And I agree, simple, right.
 
But check this one out…
 
Say we want to build a custom component wrapper for a form field...like say a name-field component that we can wrap around an input of type text and display a message as the user changes the value in the field.
 
In that name field component, we can use @ContentChild() to query for a NgControl…
 
And then in the ngAfterContentInit lifecycle method we can subscribe to valueChanges off of that control.
 
And guess what...this works for both Template and Reactive!
 
So we just found a way to subscribe to valueChanges for Template form models.
 
And remember, Template form models don’t get created until Angular processes the component, so we need to wait for the ngAfterContentInit lifecycle to get a hold of this thing.
 
Now, in full disclosure here...this works because this component is receiving the form field from the parent component, which is the one responsible for wiring it up to the template forms directive.
 
And because that component gets processed first, the Template directives will have run and ticked and the underlying form control will be available by the time this component’s ngAfterContentInit runs.
 
But, that’s not to say that we can’t create custom form components that have form fields within their markup and have those work with both Template and Reactive.
 
We can leverage control value accessors and write custom components that support both.
 
And we can write these in a way that is not directly tied to Template or Reactive form directives sets. We just need to do the plumbing ourselves.
 
What I mean by that is this...if we have a custom component that will render an input of type text, we just need to handle getting the value updates wired up to the methods we need implemented to satisfy a control value accessor.
 
And from there we can wire up in the parent markup the same way we do for native form elements for Template and Reactive respectively.
 
And we can use validators on these, right next to the ngModel or formControlName.
 
And in the custom component, we can use ContentChild(NgControl) to query for the wired up control...because ContentChild actually works for children that end up in an ng-content element via content projection and it works for things on the host
 
And then in the markup of that custom element, we can use that control class field to check the validity and make display decisions.
 
And this works for both Template and Reactive.
 
 
Now, should we be going out of our way to be building stuff that works for each and trying to make the code and architecture across the board as similar as possible?
 
If we’re building a reusable component library, then probably.
 
But for our own app stuff. It’s maybe going too far. 
 
But honestly, it’s a bit of a challenge for us when it comes to building forms in Angular, having these two different ways to pick from. Especially when they don’t appear to be that drastically different from one another.
 
So, I know, you’re all like “come on Schwarty, guidance...throw us something here!”
 
Alright, well let me pull up that little list we made...
 
Okay what it comes down to is this…
 
Template Forms provides a way to build forms light and quick, in the similar fashion that AngularJS provides us.
 
Think of it as an API abstraction for Reactive Forms. Under the hood, all the reactive stuff is there. 
 
We just don’t need to do all that setup to get started with it.
 
But there is a good chance that we will end up in Reactive Forms. It doesn’t take much form complexity or rules before we find yourself wanting more control and needing access to that underlying form model early in an easy manner.
 
So…
 
if we’re porting over from an AngularJS application or we have data models already written that contain built in validation and value changes logic then I would say choose Template Forms.
 
Otherwise, we should dive into Reactive Forms. Even if we have something as simple as an email newsletter signup form, using Reactive Forms is easy to get started with and will set us up for future expansion.
 
And with that, we have accepted the reality that there are these two ways to do forms and we have gained a solid understanding of what is really going on here with both…
 
And we are now in a good position to make sound decisions on this forms stuff as we leave port and set sail on our journey across the seas of data collection.
 
Thank you.
