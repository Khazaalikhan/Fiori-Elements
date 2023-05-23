Look at the service EstablIshed

Create a Metadata file for Travel Entity

	Layer : #Core -> #customer ( Low -> HIgh precedence )
	
	@UI.lineItem: [ { position : 10, Importance : #High }]  --- visible when screen sixe is small too
  
	Filter --> @UI.selectionField : [ { position : 20 } ]
  
Header Info

	@UI : { headerInfo : 
		{ typeName : 'Travel',
		  typeNamePlural : 'Travels' }
	        presentationVariant : [ {
            sortOrder : [ { by : 'TravelID'
                            direction : #ASC 
                        } ]
            visualizations: [{ type: #AS_LINEITEM }] }

Refine column having ID

	@EndUserText.label: 'Travel' --- Replacement header column
	@ObjectModel.text.element : [ 'Description' ] --- Source for replacement
	
	@EndUserText.label: 'Customer'
	@ObjectModel.text.element: ['Lastname']
	
Value Help

	@Consumption.ValueHelpDefinition : [ { 
		entity : { name : '\DMO\I_Customer', 
		           element : 'CustomerID' }  } ]
							 
Value Help as Drop Down

	@ObjectModel.resultSet.sizeCategory : #XS
	
Description Instead of codes

	@UI.textArrangement : #TEXT_ONLY
	
Conditional Status Emphasis ( Criticality )

	->Define New field in CDS to hold the value in colour
		0 -- Unknown
		1 -- Red
		2 -- Green
		3 -- Yellow
		
	-> @UI.lineItem : [ { position : 80, criticality : 'new_field' } ]
