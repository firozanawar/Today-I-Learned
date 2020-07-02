### Android

Case : Let us suppose you have 5 fragments but your Bottom Navigation View shows only 3, so rest of the 2 fragment should not be having the bottomNavigationView. In that case we can use "addOnDestinationChangedListener" to control the visibility. Code snippets is below..

// Setup the toolbar
setSupportActionBar(toolbar)

// Setup the bottom navigation menu for Navigation Component
bottomNavigationView.setupWithNavController(navHostFragment.findNavController())

// Control the visibility
navHostFragment.findNavController()
            .addOnDestinationChangedListener { _, destination, _ ->
                when (destination.id) {
                    R.id.runFragment, R.id.statisticsFragment, R.id.settingFragment ->
                        bottomNavigationView.visibility = View.VISIBLE
                    else -> bottomNavigationView.visibility = View.GONE
                }
            }