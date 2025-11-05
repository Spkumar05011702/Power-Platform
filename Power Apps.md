## Power Apps Formula 

          //Get Environment Base URL
          varEnvironmentBaseURL = LookUp('Environment Variable Values','Environment Variable Definition'.'Schema Name' = "pgimre_envCurrentEnvironmentURL").Value;
          
          //security roles related code
          varFundPerformanceBORole = LookUp('Environment Variable Values','Environment Variable Definition'.'Schema Name' = "pgimre_envFundPerformanceBusinessAppOwner").Value;
           
          varFundPerformanceSPORole = LookUp('Environment Variable Values','Environment Variable Definition'.'Schema Name' = "pgimre_envFundPerformanceSystemsProductOwner").Value;
           
          varFundPerformanceMemberRole = LookUp('Environment Variable Values','Environment Variable Definition'.'Schema Name' = "pgimre_envFundPerformanceMember").Value;
           
          varFundPerformanceViewerRole = LookUp('Environment Variable Values','Environment Variable Definition'.'Schema Name' = "pgimre_envFundPerformanceViewer").Value;
          
          
         colUserRoles = ShowColumns(
             LookUp(
                 Users,
                 'Azure AD Object ID' = User().EntraObjectId
             ).'Teams (teammembership_association)',
             'Team Name'
         );
          
         //Role check
         varUserhasFPBORole = !IsBlank(LookUp(colUserRoles,name = varFundPerformanceBORole));
         varUserhasFPSPORole = !IsBlank(LookUp(colUserRoles,name = varFundPerformanceSPORole));
         varUserhasFPMemberRole = !IsBlank(LookUp(colUserRoles,name = varFundPerformanceMemberRole));
         varUserhasFPViewerRole = !IsBlank(LookUp(colUserRoles,name = varFundPerformanceViewerRole));
          
         //Admin Roles
         isAdmin = varUserhasFPBORole || varUserhasFPSPORole;
         isApprover = varUserhasFPBORole || varUserhasFPSPORole || varUserhasFPMemberRole;
         isReadOnlyUser = varUserhasFPMemberRole || varUserhasFPViewerRole;
          
         //Centralized Font
         //varFontFamily=Font.'Open Sans';
          
         //Theme color
         //Styling
         F = Font.'Open Sans';
         FS = {
             Body:15,
             Header:24,
             SubHeader:20
         };
         C = { //Color Palette
             P: { //Primary
                 A: ColorValue("#002247"), //Dark navy
                 B: ColorValue("#E3B449"), //Mustard
                 C: ColorValue("#0CA0EB"), //Bright Blue
                 D: ColorValue("#E8F5FA"), //light blue
                 E:  Color.White, //White
                 F: ColorValue("#013369"),//Header Background Color
                 G: RGBA(0, 120, 215, 1),
                 H:RGBA(0, 0, 0, 1), // Text color
                 I: RGBA(80, 80, 80, .7), // Charcol Dark gray, excellent for white text
                 J: RGBA(112, 128, 144, 1), //Slightly bluish gray, modern look
                 K: RGBA(120, 120, 120, 1), // Darker gray, good contrast
                 L : Color.Black,
                 M: RGBA(0, 0, 139, 1) //Color for hyperlink
             },
             N:{ //Neutrals
                 A: ColorValue("#f9fafb"),//light background container fill
                 B: ColorValue("#9ca3b0"), //icons and borders
                 C: ColorValue("#384252"), //grey text
                 D: ColorFade(ColorValue("#002247"),10%),
                 E: ColorValue("#f9fafb")
             },
             G:{ //Greys
                 A: ColorValue("#EDEFF3"),//ColorFade(ColorValue("#394047"),75%),
                 B: ColorFade(ColorValue("#394047"),50%),
                 C: ColorFade(ColorValue("#394047"),25%),
                 D: ColorFade(ColorValue("#394047"),10%),
                 E: ColorFade(ColorValue("#394047"), -50%),
                 F: RGBA(237,239,243,.50),//Slightly Transparent BG
                 G: RGBA(245,245,245,100),//Control bg
                 H: RGBA(97,97,97,100) //Chevron Color/Select Item
             },
             U:{ //Utility
                 A: ColorValue("#BD2830"), //Error Red
                 B: ColorValue("#E3B449"), //Mustard
                 C: ColorValue("#0C7BC3"), //Bright Blue
                 D: ColorValue("#E8F5FA"), //light blue
                 E: ColorValue("#002247"), //Non-changing navy
                 F: ColorValue("#719A4B"), //Green
                 G: ColorValue("#84E63D"), //Light Green
                 H: ColorValue("#8046DB"), //Purple
                 I: ColorValue("#D752FD"), //Pink
                 J: ColorValue("#00748A") //Spruce
             }
         };
         G = 16; //Gutter
