# Property `css`

In many different places in the API you can use the `css` property to
change the style of HTML elements. You may for example use this property
in the very <a href="/support/json/top-level-properties">top level</a>
of the JSON document to change the style of the entire email, inside
the <a href="/support/property-content">`content`</a> property to
change the styling of the 580px wide centered content, and in many blocks
to change the styling of the blocks. This `css` JSON property expects
an object with styling properties that will be directly copied into a
`style` attribute of an HTML element.

## An important word of warning

All the CSS rules that you set in the `css` property, will be directly applied 
as inline CSS to the HTML element. When using your own custom CSS, you must be 
aware that it might break the email lay-out or responsiveness in some clients,
especially when you use more exotic css properties. We therefore advise you
not to use the `css` property at all, and stick with the tested and
documented properties.

Because the `css` property can be used in so many places, we stick here 
with just a number of examples. Keep in mind that there are many more places 
where this property can be used.

### Example 1: Specify CSS on the email template outer body table

The outer wrapper table acts like the HTML body of your email. Most email clients
will strip out the ```<body>``` tag. That's why most HTML emails, including the emails
generated with this API, have a 100% * 100% outer wrapper table. This enables you for instance
to change the background color surrounding the email. 


    {
        "from" : "info@example.com", 
        "subject" : "Example mail 1",
        "css" : {
            "background-color" : "red"
        }
    }


### Example 2: Specify CSS on the email template inner wrapper table

Emails generated by the responsiveemail.com API have a fixed width of 580px and are 
centered on the screen. It is possible to define your own custom CSS for this 
580px wrapper table, by setting the  property `css` inside the `content` property. 
CSS will be directly applied as inline CSS styling to the ```<td>``` of this table. 

    {
        "from" : "info@example.com", 
        "subject" : "Example mail 2",
        "content" : {
            "css" : {
                "border" : "2px solid red",
                "display" : "inline-block"
            }
        }
    }

### Example 3: Specify custom CSS on individual blocks in your email

The property `css` is also available in specific block within the content section. 
It will then be directly applied to the element. For instance, in an image block, 
the css specified within `img.css` will be directy applied to the html ```<img>``` 
tag. 

    {
        "from" : "info@example.com", 
        "subject" : "Example mail 3",
        "content" : {
            "blocks" : [ {
                "type" : "image",
                "img" : {
                    "css" : {
                        "margin-right" : "10px",
                        "border" : "2px dashed pink"
                    }
                }
            } ]
        }
    }
