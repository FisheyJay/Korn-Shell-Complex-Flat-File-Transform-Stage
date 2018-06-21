##################################################################################
#
# Name      : KornShellComplexFlatFileTransformer.ksh
# Author    : John Fisher
# Date      : 11.15.2006
# Purpose   : In the absence of a Complex Flat File Transform Stage in the current 
#             version of IBM Ascential (now InfoSphere) DataStage, Convert or 
#             "Transform" the yearly IBC 1099 complex flat file having 5 different 
#             record types for detail recs, subtotal recs, total recs and so on
#             (TRECORD,ARECORD,BRECORD,CRECORD,FRECORD), to the IRS Publication 
#             1220 "1099-MISC" format.
#
# License   : None, totally usable by all freely
#
# Usage     : If you find yourself in the unfortunate position of not having or 
#             being without the benefit of a robust, capable and modern ETL Tool 
#             such as IBM InfoSphere DataStage or SSIS, feel free to clone this code
#             and modify as necessary to perform transformation of complex flat files
#             having one or more types of detail records and/or one or more types of
#             subtotals records and/or one or more types of totals records.
#
##################################################################################
# Modification History:
##################################################################################
# Name:             Date:	Description:     
##################################################################################
# John Fisher       11.15.2006	Created. Generate 1099s for providers
# 			        in network providing at least one service 
# John Fisher       12.14.2006	Add Output/Working directory as a parameter. 
#                         	Check cat function return code and Echo return
#                               code when program fails for whichever reason.
# John Fisher       01.08.2007	Add conversion logic to handle negative amount
#                         	values. Actual production file contains these, 
#                               which was unexpected.
# John Fisher       01.10.2007	Place hyphen into converted file as left-most
#                         	character of negative amount value, PAD with
#                               zeroes after that. Positive numbers will be 
#                               left-padded with zeroes only. 
##################################################################################
# Use set -x to turn debugger on. Uncomment it, that is.
##################################################################################
