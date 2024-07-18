const express = require('express');
const router = express.Router();
const Discount = require('../models/discount');

// Chegirma kodlarini olish
router.get('/discounts', async (req, res) => {
    const discounts = await Discount.find();
    res.send(discounts);
});

// Yangi chegirma kodini yaratish
router.post('/discounts', async (req, res) => {
    const discount = new Discount(req.body);
    await discount.save();
    res.send(discount);
});

module.exports = router;

