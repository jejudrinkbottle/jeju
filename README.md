# jeju
midclient := midtrans.NewClient()
    midclient.ServerKey = "SB-Mid-server-vLwFbGGLj2TzJb42YLBIzzAC"
    midclient.ClientKey = "SB-Mid-client-R7OBFX9gjFOFnNd4"
    midclient.APIEnvType = midtrans.Sandbox

    coreGateway := midtrans.CoreGateway{
        Client: midclient,
    }

    chargeReq := &midtrans.ChargeReq{
        PaymentType: midtrans.SourceCreditCard,
        TransactionDetails: midtrans.TransactionDetails{
            OrderID: "12345",
            GrossAmt: 200000,
        },
        CreditCard: &midtrans.CreditCardDetail{
            TokenID: "YOUR-CC-TOKEN",
        },
        Items: &[]midtrans.ItemDetail{
            midtrans.ItemDetail{
                ID: "ITEM1",
                Price: 200000,
                Qty: 1,
                Name: "Someitem",
            },
        },
    }

    resp, _ := coreGateway.Charge(chargeReq)
