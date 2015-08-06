# indoorGPS

        /* @wsc add ibeacon validation func
        self.beaconManager.delegate = self
        self.beaconManager.requestAlwaysAuthorization()
        self.beaconManager.startMonitoringForRegion(CLBeaconRegion(
            proximityUUID: NSUUID(UUIDString: "B9407F30-F5F8-466E-AFF9-25556B57FE6D"),
            major: 5133, minor: 59699, identifier: "monitored region"))
        //self.beaconManager.stopMonitoringForRegion() */
        
        // @wsc send data to parse db
        Parse.setApplicationId("qYr3hmMq6ndfFdP56OIB5QQ90Loc0PPWXlGOMrUh", clientKey:"Neh8bvpvlSkkAUfTo4CcsHDJeM88W8q7RdXB9LqB")
        
        var coord = PFObject(className:"Coordinate")
        coord["x"] = position.x
        coord["y"] = position.y
        var now = NSDate()
        let dateFormatter = NSDateFormatter()
        dateFormatter.dateFormat = "yyyy MMM dd HH:mm:ss.SSS"
        let date = dateFormatter.stringFromDate(now)
        coord["time"] = date
        coord.saveInBackgroundWithBlock {
            (success: Bool, error: NSError?) -> Void in
            if (success) {
                // The object has been saved.
            } else {
                // There was a problem, check error.description
                println(error?.description)
            }
        }
