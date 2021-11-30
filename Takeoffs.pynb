
import os
import pandas as pd


cwd = os.path.abspath('')
files = os.listdir(cwd)
df = pd.DataFrame()
for file in files:
   if file.endswith('.xlsx'):
       df = df.append(pd.read_excel(file), ignore_index=True)
df.head()

#Save the global sheet on local drive
df.to_excel('Global.xlsx')


# drop unrequired column
df = pd.DataFrame(pd.read_excel("Global.xlsx"))
df=df.drop(columns='Canopy')

#Group to get sum of Hex Bolts,Power Washers and Nuts for the entire project
Vendor_CSV=df.groupby(by=[ "Material_Spec","Dimensions"]).sum()

#Convert to excel; Ready to send to Vendors; File saved in indicated directory
Vendor_CSV.to_excel (r'C:\Users\nkoech\Desktop\Vendor.xlsx', index = True, header=True)

#Time to RFQs
Dim=df.iloc[:,1] 
Spec=df.iloc[:,0]                      
Qty=df.iloc[:,3]

#Vendor Ready: Prints summary of quantity take-off
print(" Provide quote for SST A563 1/2_HEAVY HEX NUTS L=1/2inches  and  F436-1 1/2_WASHERS L=1/8inches (Both Quantity=%d)." % (Qty[0][1] ))

for i in range(1,20):
       print(' Quote for Domestic and Galvanized hardware for :%s %s Hex Bolt and A563DH Nuts(Both Quantity=%d), and F436 Plain Washers (Quantity=%d) '% (Dim[i][0],Spec[i][0],Qty[i][0],2*Qty[i][0] ))
